---
title : "Test gửi email cảnh báo"
date : 2026-07-01
weight : 6
chapter : false
pre : " <b> 5.5.6 </b> "
---

1. **Mở Publish message**
   * Trong trang topic `energy-waste-alert-topic`, bấm **Publish message**.

2. **Điền nội dung tin nhắn**
   * Subject:

```
Test energy waste alert
```

   * Message body:

```json
{
  "alertType": "ENERGY_WASTE",
  "roomId": "lab-01",
  "deviceId": "aircon-01",
  "deviceStatus": "ON",
  "occupancy": false,
  "powerW": 180,
  "message": "Test alert from Amazon SNS for Smart Home Energy Waste Monitoring System."
}
```

3. **Gửi tin nhắn**
   * Bấm **Publish message**.

![Publish message to topic](/images/5-Workshop/5.5-sns/pic7.png)
