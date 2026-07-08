---
title : "Verify DynamoDB"
date : 2026-07-05
weight : 4
chapter : false
pre : " <b> 5.10.4 </b> "
---

This step is to compare logs with actual data.

1. Open a new AWS Console tab.
2. Search for: **DynamoDB**.
3. Choose: **Tables** -> select table `EnergyWasteData`.
4. Click: **Explore table items** -> Click **Run** (or Scan).
5. Search for items with `PK = ROOM#lab-01`.
6. Check for different sort key types: `PROFILE`, `TELEMETRY#...`, `ALERT#...`.
7. **Telemetry Data**:
   * Open a newly created item and verify: `sensorId = virtual-sensor-01`, `roomId = lab-01`, `deviceStatus = ON or OFF`, and `source = eventbridge-scheduler`.
8. **Alert Data** (if any):
   * Open an `ALERT#...` item and check: `roomId = lab-01`, `deviceStatus = ON`, `occupancy = false`, `powerW >= 120`.

![DynamoDB Verification](/images/5-Workshop/5.10-CloudWatch/04-dynamodb-core-result.png)