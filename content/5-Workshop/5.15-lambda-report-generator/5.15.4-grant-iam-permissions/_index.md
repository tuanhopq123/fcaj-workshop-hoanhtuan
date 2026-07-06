---
title : "Grant IAM Permissions"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.15.4. </b> "
---

The Lambda function requires specific permissions to interact with other AWS services:
- `dynamodb:Query`: To read TELEMETRY and ALERT data.
- `dynamodb:PutItem`: To save report metadata.
- `s3:PutObject`: To save the generated JSON file to S3.
- `AWSLambdaBasicExecutionRole`: To write logs to CloudWatch.

#### Step 1: Open Execution Role

1. In your `energy-report-generator` Lambda function, select the **Configuration** tab.
2. In the left menu, choose **Permissions**.
3. Under the **Execution role** section, click on the blue role name (e.g., `energy-report-generator-role-xxxxxxxx`).
4. The IAM Management Console will open in a new tab.

#### Step 2: Check CloudWatch Permissions

1. In the **Permissions policies** section, verify if the `AWSLambdaBasicExecutionRole` policy is attached.
2. If it is already attached, skip to the next step.
3. If not, click **Add permissions** -> **Attach policies**, search for `AWSLambdaBasicExecutionRole`, select it, and click **Add permissions**.

#### Step 3: Create Inline Policy

1. In the IAM role, click **Add permissions** -> **Create inline policy**.
2. Select the **JSON** tab.
3. Delete the default content and paste the following JSON:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadAndWriteEnergyReportMetadata",
      "Effect": "Allow",
      "Action": [
        "dynamodb:Query",
        "dynamodb:PutItem"
      ],
      "Resource": [
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData",
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData/index/*"
      ]
    },
    {
      "Sid": "WriteEnergyReportToS3",
      "Effect": "Allow",
      "Action": [
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::energy-waste-report-347685737655-ap-southeast-1/*"
    }
  ]
}
```
1. Click Next.

2. For Policy name, enter: energy-report-generator-data-policy

3. Click Create policy.

Validation: Ensure the execution role has both AWSLambdaBasicExecutionRole and the newly created energy-report-generator-data-policy. Do not grant excessive permissions like dynamodb:*, s3:*, or AdministratorAccess.