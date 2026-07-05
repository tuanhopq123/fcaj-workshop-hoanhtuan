---
title : "Grant s3:GetObject to API Handler"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.14.7. </b> "
---

The `energy-api-handler` only needs to download the object based on an `objectKey` retrieved from metadata in DynamoDB. Therefore, the required permission is: `s3:GetObject`. 
*(Do not grant `s3:PutObject`, `s3:DeleteObject`, `s3:ListAllMyBuckets`, or `s3:*`. AWS identifies `s3:GetObject` as the mandatory permission to read an object without specifying a version ID).*

#### Open IAM Role

1. In the `energy-api-handler` Lambda, select: **Configuration** -> **Permissions**.
2. Under **Execution role**, click the blue role name. The name should look similar to: `energy-api-handler-role-xxxxxxxx`.
3. IAM will open in a new tab.

#### Create a Separate Inline Policy for S3

1. Click **Add permissions** -> **Create inline policy**.
2. Select the **JSON** tab.
3. Delete the sample JSON.
4. Paste the following policy:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadGeneratedEnergyReports",
      "Effect": "Allow",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::energy-waste-report-347685737655-ap-southeast-1/*"
    }
  ]
}

*Note the `/*` at the end of the ARN (`arn:aws:s3:::energy-waste-report-347685737655-ap-southeast-1/*`). It represents the objects inside the bucket. The execution role is the mechanism that grants Lambda permission to access other AWS resources; thus, the S3 read permission must reside in the role of the energy-api-handler.*

5. Click **Next**.
6. For **Policy name**, enter: `energy-api-handler-s3-read-policy`
7. Click **Create policy**.

#### Expected Results
The execution role must have exactly three policies attached:
1. `AWSLambdaBasicExecutionRole`
2. `energy-api-handler-dynamodb-read-policy`
3. `energy-api-handler-s3-read-policy`

![Grant S3 Permission](/images/5-Workshop/5.14-s3-report/5.14.7-iam-s3.png)