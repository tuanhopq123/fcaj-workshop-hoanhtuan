---
title : "Add Bucket to Lambda API Handler"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.14.6. </b> "
---

The `energy-api-handler` Lambda needs to know which bucket contains the reports.

#### Add Environment Variable

1. Navigate to **Lambda** -> **Functions** -> **energy-api-handler**.
2. Select the **Configuration** tab, then choose **Environment variables**.
3. Click **Edit**.
4. Keep the four existing variables unchanged:
   - `DDB_TABLE` = `EnergyWasteData`
   - `DEFAULT_ROOM_ID` = `lab-01`
   - `DEFAULT_LIMIT` = `50`
   - `REPORTS_PK` = `REPORTS`
5. Click **Add environment variable**.
6. Enter the following details:
   - **Key**: `REPORT_BUCKET`
   - **Value**: `energy-waste-report-347685737655-ap-southeast-1`
7. Click **Save**.

#### Expected Results
The Lambda function must now have five environment variables:
- `DDB_TABLE` = `EnergyWasteData`
- `DEFAULT_ROOM_ID` = `lab-01`
- `DEFAULT_LIMIT` = `50`
- `REPORTS_PK` = `REPORTS`
- `REPORT_BUCKET` = `energy-waste-report-347685737655-ap-southeast-1`

![Add Bucket to API Handler](/images/5-Workshop/5.14-s3-report/5.14.6-add-env.png)