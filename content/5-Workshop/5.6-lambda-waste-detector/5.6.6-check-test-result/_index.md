---
title : "Check the Test Result"
date : 2026-07-01
weight : 6
chapter : false
pre : " <b> 5.6.6 </b> "
---

1. **Review the execution result**
   * After running the test, check the **Execution results** panel.
   * The status should be `Succeeded`, and the response should look like this:

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

![Test result - Succeeded](/images/5-Workshop/5.6-lambda/pic10.png)
