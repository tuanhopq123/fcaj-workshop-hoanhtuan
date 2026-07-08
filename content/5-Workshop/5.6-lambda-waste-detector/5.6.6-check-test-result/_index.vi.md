---
title : "Kiểm tra kết quả Test"
date : 2026-07-01
weight : 6
chapter : false
pre : " <b> 5.6.6 </b> "
---

1. **Xem kết quả thực thi**
   * Sau khi chạy test, kiểm tra panel **Execution results**.
   * Trạng thái phải là `Succeeded`, và response sẽ có dạng:

```json
{
  "statusCode": 200,
  "body": {
    "message": "Telemetry processed successfully",
    "isWaste": true,
    "alertSent": true,
    "roomId": "lab-01",
    "deviceId": "aircon-01",
    "powerW": 180
  }
}
```

![Kết quả test - Succeeded](/images/5-Workshop/5.6-lambda/pic10.png)
