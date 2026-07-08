---
title : "Test Lambda Waste Detector"
date : 2026-07-01
weight : 5
chapter : false
pre : " <b> 5.6.5 </b> "
---

1. **Mở tab Test**
   * Trong trang Lambda, bấm **Test**.
   * Chọn **Create new event**.

2. **Cấu hình test event**
   * Event name: `test_waste_event`
   * Event JSON:

```json
{
  "sensorId": "virtual-sensor-01",
  "roomId": "lab-01",
  "timestamp": "2026-07-01T10:00:00Z",
  "deviceId": "aircon-01",
  "deviceName": "Air Conditioner",
  "deviceStatus": "ON",
  "occupancy": false,
  "powerW": 180,
  "voltageV": 220,
  "currentA": 0.82,
  "energyKwh": 1.25
}
```

3. **Lưu và chạy test**
   * Bấm **Save**.
   * Sau đó bấm **Test**.

![Create new test event - test_waste_event](/images/5-Workshop/5.6-lambda/pic9.png)
