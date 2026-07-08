---
title : "Test MQTT Message"
date : 2026-07-05 
weight : 4
chapter : false
pre : " <b> 5.8.4 </b> "
---

Bây giờ ta sẽ publish thủ công một message để kiểm tra:

1. Trong AWS IoT Core, chọn menu bên trái: **Test**.
2. Chọn: **MQTT test client**.
3. **Bước 2: Subscribe topic**
   + Chọn tab: **Subscribe to a topic**.
   + Tại **Topic filter**, nhập: `home/lab/telemetry`.
   + Nếu có mục QoS, chọn: **QoS 0**.
   + Bấm: **Subscribe**.
   + Bên trái hoặc phía dưới phải xuất hiện subscription: `home/lab/telemetry`.

![Subscribe](/images/5-Workshop/5.8-AWS-IoT-Core/MQTT test client1.png)

4. **Bước 3: Publish message**
   + Chọn tab: **Publish to a topic**.
   + Tại **Topic name**, nhập: `home/lab/telemetry`.
   + Nếu có QoS, chọn: **0**.
   + Nếu có Retain message, giữ: **Off**.
   + Xóa payload mẫu và dán:

    {
      "sensorId": "manual-iot-test-01",
      "roomId": "lab-01",
      "timestamp": "2026-07-03T03:00:00Z",
      "deviceId": "aircon-01",
      "deviceName": "Air Conditioner",
      "deviceStatus": "ON",
      "occupancy": false,
      "powerW": 200,
      "voltageV": 220,
      "currentA": 0.91,
      "energyKwh": 1.5
    }

   + Bấm: **Publish**.

![Publish](/images/5-Workshop/5.8-AWS-IoT-Core/02-mqtt-test-message1.png)