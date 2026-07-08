---
title : "Test Sending an Alert Email"
date : 2026-07-01
weight : 6
chapter : false
pre : " <b> 5.5.6 </b> "
---

1. **Open Publish message**
   * On the `energy-waste-alert-topic` page, click **Publish message**.

2. **Fill in the message**
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

3. **Publish the message**
   * Click **Publish message**.

![Publish message to topic](/images/5-Workshop/5.5-sns/pic7.png)
