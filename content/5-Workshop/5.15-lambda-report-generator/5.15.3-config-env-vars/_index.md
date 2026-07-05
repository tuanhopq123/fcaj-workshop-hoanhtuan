---
title : "Configure Environment Variables"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.15.3. </b> "
---

The Lambda function needs to know the DynamoDB table name, S3 bucket name, default room, and report storage prefix to operate correctly.

#### Step 1: Open Environment variables

1. In your `energy-report-generator` Lambda function.
2. Select the **Configuration** tab.
3. In the left menu, choose **Environment variables**.
4. Click **Edit**.

#### Step 2: Add Environment Variables

Click **Add environment variable** for each of the following configurations:

1. **DDB_TABLE**
   - Key: `DDB_TABLE`
   - Value: `EnergyWasteData`
2. **REPORT_BUCKET**
   - Key: `REPORT_BUCKET`
   - Value: `energy-waste-report-347685737655-ap-southeast-1`
   - *(Note: Do not enter the `s3://` prefix, only the bucket name).*
3. **REPORTS_PK**
   - Key: `REPORTS_PK`
   - Value: `REPORTS`
4. **DEFAULT_ROOM_ID**
   - Key: `DEFAULT_ROOM_ID`
   - Value: `lab-01`
5. **REPORT_PREFIX**
   - Key: `REPORT_PREFIX`
   - Value: `reports`

#### Step 3: Save Configuration

Verify that all five variables are correctly entered, then click **Save**.

*Security Note: Do not place sensitive information such as AWS access keys, JWTs, Cognito passwords, or Client secrets in Environment Variables. Lambda will use temporary AWS credentials from its execution role.*

![Configure Environment Variables](/images/5-Workshop/5.15-lambda-report/5.15.3-env-vars.png)