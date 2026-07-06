---
title: "5.6.4 Deploy test"
weight: 1
---

# 5.6.4 Triển khai mã nguồn và Kiểm thử hệ thống

Sau khi hoàn tất cấu hình hệ thống và phân quyền bảo mật, chúng ta tiến hành dán tập lệnh logic xử lý core Python vào hàm Lambda, thực hiện chạy thử với dữ liệu giả lập và xác minh kết quả tại các dịch vụ đầu ra.

### Các bước thực hiện:

1. Quay lại trang quản lý hàm Lambda **energy-waste-detector**, di chuyển và nhấn chọn tab **Code**.
2. Tại sơ đồ thư mục tệp tin bên trái, nhấp đúp để mở tệp `lambda_function.py`.
3. Chọn và xóa sạch mã nguồn giữ chỗ mặc định bên trong trình duyệt, sau đó dán toàn bộ đoạn mã logic xử lý cốt lõi dưới đây:

```python
import json
import os
import uuid
from datetime import datetime, timezone
from decimal import Decimal

import boto3


DDB_TABLE = os.environ.get("DDB_TABLE", "EnergyWasteData")
SNS_TOPIC_ARN = os.environ.get("SNS_TOPIC_ARN", "")
POWER_THRESHOLD_W = float(os.environ.get("POWER_THRESHOLD_W", "120"))

dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)
sns = boto3.client("sns")


def now_utc_iso():
    return datetime.now(timezone.utc).isoformat().replace("+00:00", "Z")


def to_dynamodb_value(value):
    if isinstance(value, float):
        return Decimal(str(value))

    if isinstance(value, dict):
        return {k: to_dynamodb_value(v) for k, v in value.items()}

    if isinstance(value, list):
        return [to_dynamodb_value(v) for v in value]

    return value


def parse_bool(value):
    if isinstance(value, bool):
        return value

    if isinstance(value, str):
        return value.strip().lower() in ["true", "1", "yes", "y", "on"]

    return bool(value)


def lambda_handler(event, context):
    print("Received event:")
    print(json.dumps(event, ensure_ascii=False))

    timestamp = event.get("timestamp") or now_utc_iso()

    room_id = event.get("roomId", "lab-01")
    sensor_id = event.get("sensorId", "virtual-sensor-01")
    device_id = event.get("deviceId", "unknown-device")
    device_name = event.get("deviceName", device_id)

    device_status = str(event.get("deviceStatus", "UNKNOWN")).strip().upper()
    occupancy = parse_bool(event.get("occupancy", True))
    power_w = float(event.get("powerW", 0))
    voltage_v = float(event.get("voltageV", 220))
    current_a = float(event.get("currentA", 0))
    energy_kwh = float(event.get("energyKwh", 0))

    is_waste = (
        device_status == "ON"
        and occupancy is False
        and power_w >= POWER_THRESHOLD_W
    )

    telemetry_item = {
        "PK": f"ROOM#{room_id}",
        "SK": f"TELEMETRY#{timestamp}#{sensor_id}",
        "entityType": "Telemetry",
        "roomId": room_id,
        "sensorId": sensor_id,
        "deviceId": device_id,
        "deviceName": device_name,
        "deviceStatus": device_status,
        "occupancy": occupancy,
        "powerW": power_w,
        "voltageV": voltage_v,
        "currentA": current_a,
        "energyKwh": energy_kwh,
        "timestamp": timestamp,
        "isWaste": is_waste,
        "source": "lambda-test-or-iot-core"
    }

    table.put_item(Item=to_dynamodb_value(telemetry_item))
    print("Telemetry stored in DynamoDB.")

    alert_sent = False

    if is_waste:
        alert_id = str(uuid.uuid4())[:8]

        message = (
            f"Energy waste detected in room {room_id}. "
            f"Device {device_name} is ON, room is empty, "
            f"power is {power_w}W, threshold is {POWER_THRESHOLD_W}W."
        )

        alert_item = {
            "PK": f"ROOM#{room_id}",
            "SK": f"ALERT#{timestamp}#{alert_id}",
            "entityType": "Alert",
            "alertId": alert_id,
            "roomId": room_id,
            "sensorId": sensor_id,
            "deviceId": device_id,
            "deviceName": device_name,
            "severity": "HIGH",
            "alertType": "ENERGY_WASTE",
            "message": message,
            "powerW": power_w,
            "thresholdW": POWER_THRESHOLD_W,
            "deviceStatus": device_status,
            "occupancy": occupancy,
            "timestamp": timestamp,
            "status": "OPEN"
        }

        table.put_item(Item=to_dynamodb_value(alert_item))
        print("Alert stored in DynamoDB.")

        if SNS_TOPIC_ARN:
            sns.publish(
                TopicArn=SNS_TOPIC_ARN,
                Subject="[AWS Energy Waste Alert]",
                Message=json.dumps(alert_item, indent=2, ensure_ascii=False, default=str)
            )
            alert_sent = True
            print("Alert email published to SNS.")

    return {
        "statusCode": 200,
        "body": {
            "message": "Telemetry processed successfully",
            "isWaste": is_waste,
            "alertSent": alert_sent,
            "roomId": room_id,
            "deviceId": device_id,
            "powerW": power_w
        }
    }