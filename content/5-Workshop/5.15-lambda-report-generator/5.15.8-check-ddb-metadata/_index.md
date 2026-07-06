---
title : "Check Metadata in DynamoDB"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.15.8. </b> "
---

#### Step 1: Open the Table

1. Navigate to **DynamoDB** -> **Tables** -> **EnergyWasteData**.
2. Click on **Explore table items**.
3. You can select **Scan** and click **Run**.
4. Alternatively, select **Query** mode and enter: `PK = REPORTS`

#### Step 2: Find Metadata

1. Locate the item with the following keys:
   - `PK` = `REPORTS`
   - `SK` = `REPORT#2026-07-03`
2. Open the item and verify that it contains the following fields:
   - `date`
   - `roomId`
   - `bucket`
   - `objectKey`
   - `fileName`
   - `contentType`
   - `generatedAt`
   - `telemetryCount`
   - `alertCount`
   - `wasteCount`
   - `totalEnergyKwh`
   - `averagePowerW`
   - `maxPowerW`

*Validation: The `objectKey` value must exactly match:* `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

![Check Metadata in DynamoDB](/images/5-Workshop/5.15-lambda-report/5.15.8-ddb-metadata.png)