---
title : "Create Test Event"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.15.6. </b> "
---

The current system data was generated on `2026-07-03`. Therefore, we will use this date for testing. 

*Note: If your DynamoDB items have a different date, replace `reportDate` with the exact date appearing in your `TELEMETRY#...` sort key.*

#### Step 1: Open Test Tab

1. In your `energy-report-generator` Lambda function.
2. Select the **Test** tab.
3. Choose **Create new event**.

#### Step 2: Enter Test Event Details

1. For **Event name**, enter: `manual_generate_report_2026_07_03`
2. Paste the following JSON payload:

{
  "source": "manual-test",
  "reportDate": "2026-07-03",
  "roomId": "lab-01"
}

3. Click **Save**.
4. Then, click the **Test** button.

#### Expected Results

The **Execution result** must display: `Succeeded`

The **Response** must contain:
- `statusCode` = `200`
- `success` = `true`
- `reportDate` = `2026-07-03`
- `roomId` = `lab-01`
- `bucket` = `energy-waste-report-347685737655-ap-southeast-1`
- `objectKey` must look similar to: `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

The `summary` section must contain:
- `telemetryCount`
- `alertCount`
- `wasteCount`
- `totalEnergyKwh`
- `averagePowerW`
- `maxPowerW`

**Troubleshooting:**
If the result shows `"telemetryCount": 0`, please check the sort key of your data in DynamoDB. For example, if your sort key is `TELEMETRY#2026-07-02T...`, you need to change your test event to match that date:

{
  "source": "manual-test",
  "reportDate": "2026-07-02",
  "roomId": "lab-01"
}

![Create Test Event](/images/5-Workshop/5.15-lambda-report/5.15.6-test-event.png)