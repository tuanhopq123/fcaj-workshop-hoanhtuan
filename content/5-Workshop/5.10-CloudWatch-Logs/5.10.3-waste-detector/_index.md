---
title : "Check Waste Detector Logs"
date : 2026-07-05
weight : 3
chapter : false
pre : " <b> 5.10.3 </b> "
---

1. Go back to: **CloudWatch → Logs → Log groups**.
2. Choose: `/aws/lambda/energy-waste-detector`.
3. Select the log stream with the newest **Last event time**. Select the time range: **Last 1 hour** or **Last 3 hours**.
4. In the filter box, enter: `Received event`.
5. You should see input data containing fields like: `sensorId`, `roomId`, `timestamp`, `deviceStatus`, `occupancy`, `powerW`.
6. Then look for equivalent lines:
   * `Telemetry stored in DynamoDB`.
   * (If waste is detected): `Alert stored in DynamoDB` and `Alert email published to SNS`.

{{% notice note %}}
Because the payload uses `forceWaste: false`, sensor data is randomly generated and not every invocation will meet the warning condition. It is normal if there are no ALERT logs and no emails sent.
{{% /notice %}}

![Waste Detector Logs Details](/images/5-Workshop/5.10-CloudWatch/03-waste-detector-logs1.png)