---
title : "Deploy Source Code"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.15.5. </b> "
---

The source code will perform the following actions:
- Receive `reportDate` during manual testing.
- If no `reportDate` is provided, it defaults to the previous day according to UTC+7.
- Query `TELEMETRY#YYYY-MM-DD`.
- Query `ALERT#YYYY-MM-DD`.
- Aggregate power and energy consumption.
- Generate a JSON report file.
- Write the file to S3.
- Write report metadata to DynamoDB.

**Naming Conventions:**
- File name: `energy-report-<roomId>-<YYYY-MM-DD>.json` (e.g., `energy-report-lab-01-2026-07-03.json`)
- Object key: `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

#### Step 1: Open Code Source

1. Go back to your `energy-report-generator` Lambda function.
2. Select the **Code** tab.
3. Open the `lambda_function.py` file.
4. Delete all the default sample code.

#### Step 2: Paste the Source Code

Copy and paste the following entire Python code:

```python
import json
import os
from datetime import date, datetime, timedelta, timezone
from decimal import Decimal, InvalidOperation
from typing import Any

import boto3
from boto3.dynamodb.conditions import Key
from botocore.exceptions import ClientError


# ============================================================
# Cấu hình
# ============================================================

DDB_TABLE = os.environ["DDB_TABLE"]
REPORT_BUCKET = os.environ["REPORT_BUCKET"]
REPORTS_PK = os.environ.get("REPORTS_PK", "REPORTS")
DEFAULT_ROOM_ID = os.environ.get("DEFAULT_ROOM_ID", "lab-01")
REPORT_PREFIX = os.environ.get("REPORT_PREFIX", "reports").strip("/")

# Việt Nam sử dụng UTC+7
LOCAL_TIMEZONE = timezone(timedelta(hours=7))

# Cảm biến ảo hiện được thiết kế gửi một mẫu mỗi phút
SAMPLING_INTERVAL_MINUTES = Decimal("1")


# Khởi tạo bên ngoài handler để tái sử dụng kết nối
dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)

s3_client = boto3.client("s3")


# ============================================================
# Hàm hỗ trợ
# ============================================================

def json_default(value: Any):
    """
    Chuyển Decimal của DynamoDB thành kiểu JSON hợp lệ.
    """
    if isinstance(value, Decimal):
        if value % 1 == 0:
            return int(value)
        return float(value)

    raise TypeError(
        f"Không thể chuyển kiểu {type(value).__name__} sang JSON"
    )


def utc_timestamp() -> str:
    """
    Trả thời gian UTC theo ISO 8601.
    """
    return (
        datetime.now(timezone.utc)
        .isoformat(timespec="milliseconds")
        .replace("+00:00", "Z")
    )


def previous_local_date() -> str:
    """
    Trả ngày hôm trước theo múi giờ Việt Nam.
    Schedule chạy lúc 00:05 sẽ tạo báo cáo của ngày vừa kết thúc.
    """
    local_today = datetime.now(LOCAL_TIMEZONE).date()
    return (local_today - timedelta(days=1)).isoformat()


def validate_report_date(value: str) -> str:
    """
    Kiểm tra ngày theo định dạng YYYY-MM-DD.
    """
    try:
        parsed_date = date.fromisoformat(value)
    except (TypeError, ValueError) as error:
        raise ValueError(
            "reportDate phải có định dạng YYYY-MM-DD."
        ) from error

    if parsed_date.isoformat() != value:
        raise ValueError(
            "reportDate phải có định dạng YYYY-MM-DD."
        )

    return value


def to_decimal(value: Any) -> Decimal:
    """
    Chuyển số về Decimal để tương thích DynamoDB.
    """
    if value is None:
        return Decimal("0")

    if isinstance(value, Decimal):
        return value

    try:
        return Decimal(str(value))
    except (InvalidOperation, TypeError, ValueError):
        return Decimal("0")


def get_item_value(item: dict, field_name: str):
    """
    Đọc field trực tiếp hoặc trong object telemetry/data/payload.
    """
    if field_name in item:
        return item.get(field_name)

    for container_name in ("telemetry", "data", "payload"):
        container = item.get(container_name)
        if isinstance(container, dict) and field_name in container:
            return container.get(field_name)

    return None


def query_items_by_date(
    room_id: str,
    item_prefix: str,
    report_date: str
):
    """
    Query tất cả item của một ngày theo sort key prefix.
    Ví dụ:
    TELEMETRY#2026-07-03
    ALERT#2026-07-03
    """
    items = []

    query_arguments = {
        "KeyConditionExpression": (
            Key("PK").eq(f"ROOM#{room_id}")
            & Key("SK").begins_with(
                f"{item_prefix}#{report_date}"
            )
        ),
        "ScanIndexForward": True
    }

    while True:
        response = table.query(**query_arguments)
        items.extend(response.get("Items", []))

        last_evaluated_key = response.get(
            "LastEvaluatedKey"
        )

        if not last_evaluated_key:
            break

        query_arguments["ExclusiveStartKey"] = (
            last_evaluated_key
        )

    return items


def build_summary(telemetry_items: list, alert_items: list):
    """
    Tổng hợp các chỉ số chính trong ngày.
    """
    power_values = []
    energy_values = []

    for item in telemetry_items:
        power_value = get_item_value(item, "powerW")
        energy_value = get_item_value(item, "energyKwh")

        if power_value is not None:
            power_values.append(to_decimal(power_value))

        if energy_value is not None:
            energy_values.append(to_decimal(energy_value))

    total_power = sum(power_values, Decimal("0"))

    if energy_values:
        total_energy = sum(
            energy_values,
            Decimal("0")
        )
    else:
        total_energy = (
            total_power
            * SAMPLING_INTERVAL_MINUTES
            / Decimal("60")
            / Decimal("1000")
        )

    if power_values:
        average_power = (
            total_power / Decimal(len(power_values))
        ).quantize(Decimal("0.01"))

        maximum_power = max(power_values).quantize(
            Decimal("0.01")
        )
    else:
        average_power = Decimal("0")
        maximum_power = Decimal("0")

    return {
        "telemetryCount": len(telemetry_items),
        "alertCount": len(alert_items),
        "wasteCount": len(alert_items),
        "totalEnergyKwh": total_energy.quantize(
            Decimal("0.00001")
        ),
        "averagePowerW": average_power,
        "maxPowerW": maximum_power
    }


# ============================================================
# Lambda handler
# ============================================================

def lambda_handler(event, context):
    """
    Tạo báo cáo điện năng hằng ngày.
    """

    if not isinstance(event, dict):
        event = {}

    print(
        "Received report event:",
        json.dumps(event, ensure_ascii=False)
    )

    room_id = event.get("roomId") or DEFAULT_ROOM_ID

    requested_date = (
        event.get("reportDate")
        or previous_local_date()
    )

    try:
        report_date = validate_report_date(requested_date)
    except ValueError as error:
        print("Invalid report date:", str(error))

        return {
            "statusCode": 400,
            "success": False,
            "message": str(error)
        }

    print(
        "Generating daily report:",
        json.dumps(
            {
                "roomId": room_id,
                "reportDate": report_date
            },
            ensure_ascii=False
        )
    )

    try:
        telemetry_items = query_items_by_date(
            room_id=room_id,
            item_prefix="TELEMETRY",
            report_date=report_date
        )

        alert_items = query_items_by_date(
            room_id=room_id,
            item_prefix="ALERT",
            report_date=report_date
        )

        print(
            "DynamoDB data loaded:",
            json.dumps(
                {
                    "telemetryCount": len(telemetry_items),
                    "alertCount": len(alert_items)
                }
            )
        )

        summary = build_summary(
            telemetry_items,
            alert_items
        )

        generated_at = utc_timestamp()

        file_name = (
            f"energy-report-{room_id}-{report_date}.json"
        )

        object_key = (
            f"{REPORT_PREFIX}/{report_date}/{file_name}"
        )

        report_document = {
            "reportVersion": "1.0",
            "reportDate": report_date,
            "roomId": room_id,
            "generatedAt": generated_at,
            "summary": summary,
            "telemetry": telemetry_items,
            "alerts": alert_items
        }

        report_json = json.dumps(
            report_document,
            default=json_default,
            ensure_ascii=False,
            indent=2
        )

        s3_response = s3_client.put_object(
            Bucket=REPORT_BUCKET,
            Key=object_key,
            Body=report_json.encode("utf-8"),
            ContentType="application/json",
            ServerSideEncryption="AES256"
        )

        print(
            "Report uploaded to S3:",
            json.dumps(
                {
                    "bucket": REPORT_BUCKET,
                    "objectKey": object_key,
                    "etag": s3_response.get("ETag")
                },
                ensure_ascii=False
            )
        )

        metadata_item = {
            "PK": REPORTS_PK,
            "SK": f"REPORT#{report_date}",
            "date": report_date,
            "roomId": room_id,
            "bucket": REPORT_BUCKET,
            "objectKey": object_key,
            "fileName": file_name,
            "contentType": "application/json",
            "generatedAt": generated_at,
            "telemetryCount": summary["telemetryCount"],
            "alertCount": summary["alertCount"],
            "wasteCount": summary["wasteCount"],
            "totalEnergyKwh": summary["totalEnergyKwh"],
            "averagePowerW": summary["averagePowerW"],
            "maxPowerW": summary["maxPowerW"]
        }

        table.put_item(Item=metadata_item)

        print(
            "Report metadata stored in DynamoDB:",
            json.dumps(
                {
                    "PK": metadata_item["PK"],
                    "SK": metadata_item["SK"]
                }
            )
        )

        return {
            "statusCode": 200,
            "success": True,
            "message": "Daily energy report generated successfully",
            "reportDate": report_date,
            "roomId": room_id,
            "bucket": REPORT_BUCKET,
            "objectKey": object_key,
            "summary": summary
        }

    except ClientError as error:
        error_code = (
            error.response
            .get("Error", {})
            .get("Code", "UnknownClientError")
        )

        print(
            "AWS service error:",
            json.dumps(
                {
                    "errorCode": error_code,
                    "message": str(error)
                },
                ensure_ascii=False
            )
        )

        return {
            "statusCode": 500,
            "success": False,
            "message": "Không thể tạo báo cáo.",
            "errorCode": error_code
        }

    except Exception as error:
        print(
            "Unexpected error:",
            type(error).__name__,
            str(error)
        )

        return {
            "statusCode": 500,
            "success": False,
            "message": "Đã xảy ra lỗi nội bộ."
        }
```
#### Step 3: Deploy the Source Code
1. Click Deploy.

2. Wait for the notification: Successfully updated the function energy-report-generator.

Note: Do not click "Test" before clicking "Deploy".

![Deploy Source Code](/images/5-Workshop/5.15-lambda-report/5.15.5-deploy-code.png)