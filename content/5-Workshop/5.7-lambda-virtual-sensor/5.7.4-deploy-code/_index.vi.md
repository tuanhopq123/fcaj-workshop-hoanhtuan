---
title: "5.7.4. Triển khai Mã Nguồn Mô Phỏng"
date: 2026-07-05
weight: 4
---

Mã nguồn Python dưới đây sẽ tự động tính toán dữ liệu và giả lập ngẫu nhiên 1 trong 4 kịch bản vận hành của thiết bị phòng lab: *Thiết bị tắt*, *Có người - Thiết bị bật*, *Không có người - Công suất thấp*, và *Không có người - Thiết bị bật công suất cao (Lãng phí điện)*.

1. Quay trở lại tab **Code** của hàm Lambda `energy-virtual-sensor`.
2. Trong trình soạn thảo **Code source**, mở tệp `lambda_function.py`.
3. Xóa toàn bộ nội dung mã mặc định cũ và dán đoạn mã nguồn hoàn chỉnh dưới đây *(Xem cấu trúc hiển thị file tại tệp `04-ma-nguon-virtual-sensor.png`)*:
   ![Triển khai mã nguồn Virtual Sensor](/images/5-Workshop/5.7-lambda-virtual-sensor/04-ma-nguon-virtual-sensor.png)

```python
import json
import os
import random
from datetime import datetime, timezone
import boto3
from botocore.exceptions import BotoCoreError, ClientError

IOT_TOPIC = os.environ["IOT_TOPIC"]
DEFAULT_ROOM_ID = os.environ["DEFAULT_ROOM_ID"]
AWS_REGION = os.environ.get("AWS_REGION", "ap-southeast-1")

iot_data_client = boto3.client("iot-data", region_name=AWS_REGION)

def get_utc_timestamp():
    return datetime.now(timezone.utc).isoformat(timespec="milliseconds").replace("+00:00", "Z")

def parse_boolean(value):
    if value is True: return True
    if isinstance(value, str): return value.strip().lower() == "true"
    return False

def generate_telemetry(event):
    force_waste = parse_boolean(event.get("forceWaste", False))
    room_id = event.get("roomId") or DEFAULT_ROOM_ID
    
    if force_waste:
        scenario = "waste"
    else:
        scenario = random.choices(
            population=["device_off", "occupied", "idle_low_power", "waste"],
            weights=[15, 35, 25, 25], k=1
        )[0]

    if scenario == "device_off":
        device_status, occupancy, power_w = "OFF", False, round(random.uniform(0.2, 3.0), 2)
    elif scenario == "occupied":
        device_status, occupancy, power_w = "ON", True, round(random.uniform(80.0, 240.0), 2)
    elif scenario == "idle_low_power":
        device_status, occupancy, power_w = "ON", False, round(random.uniform(15.0, 110.0), 2)
    else:
        device_status, occupancy, power_w = "ON", False, round(random.uniform(130.0, 260.0), 2)

    voltage_v = round(random.uniform(218.0, 223.0), 1)
    current_a = round(power_w / voltage_v, 2)
    energy_kwh = round((power_w / 1000.0) / 60.0, 5)

    return {
        "sensorId": "virtual-sensor-01", "roomId": room_id, "timestamp": get_utc_timestamp(),
        "deviceId": "aircon-01", "deviceName": "Air Conditioner", "deviceStatus": device_status,
        "occupancy": occupancy, "powerW": power_w, "voltageV": voltage_v, "currentA": current_a,
        "energyKwh": energy_kwh, "scenario": scenario, "source": event.get("source", "unknown")
    }

def lambda_handler(event, context):
    if not isinstance(event, dict): event = {}
    print("Received trigger event:", json.dumps(event, ensure_ascii=False))
    telemetry = generate_telemetry(event)
    
    print("Publishing telemetry to AWS IoT Core:", json.dumps({"topic": IOT_TOPIC, "telemetry": telemetry}, ensure_ascii=False))
    payload = json.dumps(telemetry, ensure_ascii=False, separators=(",", ":")).encode("utf-8")
    
    try:
        response = iot_data_client.publish(topic=IOT_TOPIC, qos=0, payload=payload)
        publish_http_status = response.get("ResponseMetadata", {}).get("HTTPStatusCode", 200)
        print("Publish response HTTP status:", publish_http_status)
        return {
            "statusCode": 200, "message": "Telemetry published successfully", "topic": IOT_TOPIC,
            "sensorId": telemetry["sensorId"], "roomId": telemetry["roomId"], "timestamp": telemetry["timestamp"],
            "deviceStatus": telemetry["deviceStatus"], "occupancy": telemetry["occupancy"], "powerW": telemetry["powerW"],
            "telemetry": telemetry
        }
    except (ClientError, BotoCoreError) as error:
        print("Failed to publish telemetry:", str(error))
        return {"statusCode": 500, "message": "Failed to publish telemetry", "topic": IOT_TOPIC, "error": str(error)}
    except Exception as error:
        print("Unexpected error:", str(error))
        return {"statusCode": 500, "message": "Unexpected error", "topic": IOT_TOPIC, "error": str(error)}