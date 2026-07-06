---
title : "Deploy Source Code"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.13.5. </b> "
---

#### Source Code Functionality

| Route | Data Reading Mechanism |
| :--- | :--- |
| `GET /rooms` | Find items with `SK = PROFILE` |
| `GET /telemetry` | Query `PK = ROOM#<roomId>` and `SK` starting with `TELEMETRY#` |
| `GET /alerts` | Query `PK = ROOM#<roomId>` and `SK` starting with `ALERT#` |
| `GET /reports` | Query metadata with `PK = REPORTS` |
| `GET /reports/{date}` | GetItem report details by date |

*Note: DynamoDB stores numbers as the `Decimal` type. Therefore, the source code includes logic to convert `Decimal` values into `int` or `float` before returning the JSON response.*

#### Step 1: Open Code Source

1. Navigate back to your Lambda function: `energy-api-handler`.
2. Select the **Code** tab.
3. Open the `lambda_function.py` file.
4. Delete all the default sample code.

#### Step 2: Paste the Source Code

Paste your Python source code into the editor (below is the core structure initialization):

```python
import json
import os
import re
from decimal import Decimal
from typing import Any

import boto3
from boto3.dynamodb.conditions import Attr, Key
from botocore.exceptions import ClientError


# ============================================================
# Configuration
# ============================================================

DDB_TABLE = os.environ["DDB_TABLE"]
DEFAULT_ROOM_ID = os.environ.get("DEFAULT_ROOM_ID", "lab-01")
REPORTS_PK = os.environ.get("REPORTS_PK", "REPORTS")

try:
    DEFAULT_LIMIT = int(os.environ.get("DEFAULT_LIMIT", "50"))
except ValueError:
    DEFAULT_LIMIT = 50


# Initialize outside the handler to reuse connection across invocations
dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)


# ============================================================
# JSON Helper Functions
# ============================================================

def json_default(value: Any):
    """
    Convert DynamoDB Decimal types to valid JSON types.
    """
    if isinstance(value, Decimal):
        if value % 1 == 0:
            return int(value)
        return float(value)

    raise TypeError(f"Type {type(value).__name__} not serializable to JSON")
    def api_response(status_code: int, body: dict):
    """
    Tạo response theo định dạng Lambda proxy integration.
    """
    return {
        "statusCode": status_code,
        "headers": {
            "content-type": "application/json; charset=utf-8",
            "cache-control": "no-store"
        },
        "body": json.dumps(
            body,
            default=json_default,
            ensure_ascii=False
        )
    }


def get_route_key(event: dict) -> str:
    """
    Xác định route từ API Gateway HTTP API payload version 2.0.
    Đồng thời hỗ trợ test trực tiếp trên Lambda Console.
    """
    route_key = event.get("routeKey")

    if route_key:
        return route_key

    request_context = event.get("requestContext") or {}
    http_context = request_context.get("http") or {}

    method = (
        http_context.get("method")
        or event.get("httpMethod")
        or "GET"
    )

    path = (
        event.get("rawPath")
        or http_context.get("path")
        or event.get("path")
        or "/"
    )

    return f"{method} {path}"


def get_limit(query_parameters: dict) -> int:
    """
    Đọc limit từ query string và giới hạn trong khoảng 1–100.
    """
    raw_limit = query_parameters.get("limit", str(DEFAULT_LIMIT))

    try:
        limit = int(raw_limit)
    except (TypeError, ValueError):
        limit = DEFAULT_LIMIT

    return max(1, min(limit, 100))


# ============================================================
# Truy vấn DynamoDB
# ============================================================

def get_rooms():
    """
    Tìm tất cả item đại diện cho hồ sơ phòng.
    PROFILE được lưu dưới sort key SK = PROFILE.
    """
    items = []

    scan_arguments = {
        "FilterExpression": Attr("SK").eq("PROFILE")
    }

    while True:
        response = table.scan(**scan_arguments)
        items.extend(response.get("Items", []))

        last_evaluated_key = response.get("LastEvaluatedKey")

        if not last_evaluated_key:
            break

        scan_arguments["ExclusiveStartKey"] = last_evaluated_key

    items.sort(
        key=lambda item: (
            item.get("roomId")
            or item.get("PK")
            or ""
        )
    )

    return items


def get_room_series(room_id: str, sort_key_prefix: str, limit: int):
    """
    Lấy telemetry hoặc alert của một phòng.
    Kết quả mới nhất được trả về trước.
    """
    response = table.query(
        KeyConditionExpression=(
            Key("PK").eq(f"ROOM#{room_id}")
            & Key("SK").begins_with(sort_key_prefix)
        ),
        ScanIndexForward=False,
        Limit=limit
    )

    return response.get("Items", [])


def get_reports(limit: int):
    """
    Lấy danh sách metadata báo cáo.

    Metadata báo cáo sẽ được tạo ở hạng mục
    Lambda Report Generator với cấu trúc:

    PK = REPORTS
    SK = REPORT#YYYY-MM-DD
    """
    response = table.query(
        KeyConditionExpression=(
            Key("PK").eq(REPORTS_PK)
            & Key("SK").begins_with("REPORT#")
        ),
        ScanIndexForward=False,
        Limit=limit
    )

    return response.get("Items", [])


def get_report_by_date(report_date: str):
    """
    Lấy metadata báo cáo theo ngày.
    """
    response = table.get_item(
        Key={
            "PK": REPORTS_PK,
            "SK": f"REPORT#{report_date}"
        }
    )

    return response.get("Item")


# ============================================================
# Lambda Handler
# ============================================================

def lambda_handler(event, context):
    """
    Xử lý request từ API Gateway HTTP API.
    """

    if not isinstance(event, dict):
        event = {}

    route_key = get_route_key(event)
    query_parameters = event.get("queryStringParameters") or {}
    path_parameters = event.get("pathParameters") or {}

    # Chỉ ghi những thông tin an toàn, không ghi Authorization header
    print(
        "Received API request:",
        json.dumps(
            {
                "routeKey": route_key,
                "rawPath": event.get("rawPath"),
                "queryStringParameters": query_parameters,
                "pathParameters": path_parameters
            },
            ensure_ascii=False
        )
    )

    try:
        # ----------------------------------------------------
        # GET /rooms
        # ----------------------------------------------------
        if route_key == "GET /rooms":
            rooms = get_rooms()

            print(f"Rooms returned: {len(rooms)}")

            return api_response(
                200,
                {
                    "success": True,
                    "count": len(rooms),
                    "items": rooms
                }
            )

        # ----------------------------------------------------
        # GET /telemetry
        # ----------------------------------------------------
        if route_key == "GET /telemetry":
            room_id = (
                query_parameters.get("roomId")
                or DEFAULT_ROOM_ID
            )

            limit = get_limit(query_parameters)

            telemetry = get_room_series(
                room_id=room_id,
                sort_key_prefix="TELEMETRY#",
                limit=limit
            )

            print(
                f"Telemetry returned: {len(telemetry)}, "
                f"roomId={room_id}"
            )

            return api_response(
                200,
                {
                    "success": True,
                    "roomId": room_id,
                    "count": len(telemetry),
                    "items": telemetry
                }
            )

        # ----------------------------------------------------
        # GET /alerts
        # ----------------------------------------------------
        if route_key == "GET /alerts":
            room_id = (
                query_parameters.get("roomId")
                or DEFAULT_ROOM_ID
            )

            limit = get_limit(query_parameters)

            alerts = get_room_series(
                room_id=room_id,
                sort_key_prefix="ALERT#",
                limit=limit
            )

            print(
                f"Alerts returned: {len(alerts)}, "
                f"roomId={room_id}"
            )

            return api_response(
                200,
                {
                    "success": True,
                    "roomId": room_id,
                    "count": len(alerts),
                    "items": alerts
                }
            )

        # ----------------------------------------------------
        # GET /reports
        # ----------------------------------------------------
        if route_key == "GET /reports":
            limit = get_limit(query_parameters)
            reports = get_reports(limit)

            print(f"Reports returned: {len(reports)}")

            return api_response(
                200,
                {
                    "success": True,
                    "count": len(reports),
                    "items": reports,
                    "message": (
                        "Chưa có báo cáo."
                        if len(reports) == 0
                        else "Lấy danh sách báo cáo thành công."
                    )
                }
            )

        # ----------------------------------------------------
        # GET /reports/{date}
        # ----------------------------------------------------
        if route_key == "GET /reports/{date}":
            report_date = path_parameters.get("date")

            if not report_date:
                return api_response(
                    400,
                    {
                        "success": False,
                        "message": "Thiếu tham số date."
                    }
                )

            if not re.fullmatch(r"\d{4}-\d{2}-\d{2}", report_date):
                return api_response(
                    400,
                    {
                        "success": False,
                        "message": "Ngày phải có định dạng YYYY-MM-DD."
                    }
                )

            report = get_report_by_date(report_date)

            if not report:
                return api_response(
                    404,
                    {
                        "success": False,
                        "date": report_date,
                        "message": "Chưa có báo cáo cho ngày này."
                    }
                )

            return api_response(
                200,
                {
                    "success": True,
                    "item": report
                }
            )

        # ----------------------------------------------------
        # Route không tồn tại
        # ----------------------------------------------------
        return api_response(
            404,
            {
                "success": False,
                "message": "Route không tồn tại.",
                "routeKey": route_key
            }
        )

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

        return api_response(
            500,
            {
                "success": False,
                "message": "Không thể đọc dữ liệu từ AWS.",
                "errorCode": error_code
            }
        )

    except Exception as error:
        print(
            "Unexpected error:",
            str(error)
        )

        return api_response(
            500,
            {
                "success": False,
                "message": "Đã xảy ra lỗi nội bộ."
            }
        )
#### Step 3: Paste the Source Code
1. Click Deploy.

2. Wait for the notification: Successfully updated the function energy-api-handler.