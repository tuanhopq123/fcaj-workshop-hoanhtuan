---
title : "Grant DynamoDB Read Permissions"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.13.4. </b> "
---

The Lambda function needs the following permissions:
- `dynamodb:Query`
- `dynamodb:Scan`
- `dynamodb:GetItem`

*Note: `Query` is used to read telemetry and alerts based on the partition key; `Scan` is used to find `PROFILE` items for rooms; `GetItem` is used to find reports by date. A DynamoDB `Query` requires a partition key value and can optionally combine it with a `begins_with` condition on the sort key.*

#### Step 1: Open Execution Role

1. In the Lambda function, select: **Configuration** -> **Permissions**
2. Under **Execution role**, click on the blue role name. 
   *(The name typically looks like: `energy-api-handler-role-xxxxxxxx`)*
3. The IAM page will open in a new tab.

#### Step 2: Create Inline Policy

1. Click: **Add permissions** -> **Create inline policy**
2. Select the **JSON** tab.
3. Delete the default sample JSON.
4. Paste the following policy:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadEnergyWasteData",
      "Effect": "Allow",
      "Action": [
        "dynamodb:GetItem",
        "dynamodb:Query",
        "dynamodb:Scan"
      ],
      "Resource": [
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData",
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData/index/*"
      ]
    }
  ]
}

5. Click: **Next**
6. For **Policy name**, enter: `energy-api-handler-dynamodb-read-policy`
7. Click: **Create policy**

![Grant DynamoDB Read Permissions](/images/5-Workshop/5.13-lambda-api-handler/5.13.4-iam-ddb.png)