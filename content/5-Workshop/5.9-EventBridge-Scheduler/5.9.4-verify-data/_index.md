---
title : "Verify Automated Data"
date : 2026-07-05
weight : 4
chapter : false
pre : " <b> 5.9.4 </b> "
---

After the schedule is created, wait for **2–3 minutes**. Do not manually test the Lambda function during this time.

#### Check DynamoDB
1. Open a new AWS Console tab and search for **DynamoDB**.
2. Choose **Tables** -> select `EnergyWasteData`.
3. Click **Explore table items** and then **Run** (or Scan).
4. Sort or search for items with:
   * `PK = ROOM#lab-01`
   * `SK` starting with `TELEMETRY#`
5. Open the latest item and verify:
   * `sensorId = virtual-sensor-01`
   * `source = eventbridge-scheduler`

You should see multiple telemetry items generated at different timestamps.

![Verify Data](/images/5-Workshop/5.9-EventBridge/04-du-lieu-telemetry-tu-dong.png)