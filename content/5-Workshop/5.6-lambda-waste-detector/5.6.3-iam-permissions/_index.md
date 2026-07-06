---
title: "5.6.3 IAM permission"
weight: 1
---

# 5.6.3 Configure IAM Execution Permissions

By default, an AWS Lambda function does not have permission to write to DynamoDB or publish notifications to Amazon SNS. We must attach an inline security policy to grant these operational privileges.

### Step-by-Step Instructions:

1. Inside your **energy-waste-detector** function dashboard, navigate to **Configuration** -> **Permissions**.
2. Under the **Execution role** section, click on the active role name hyperlink (it will look similar to `energy-waste-detector-role-pmsoahv7`). This will safely open the IAM Management dashboard in a new tab.
3. In the IAM Role summary screen, click on **Add permissions** and select **Create inline policy** from the dropdown menu.
4. Switch the editor mode to the **JSON** tab.
5. Completely wipe out any default template content inside the editor and paste the following strict policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "WriteEnergyWasteData",
      "Effect": "Allow",
      "Action": [
        "dynamodb:PutItem"
      ],
      "Resource": "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData"
    },
    {
      "Sid": "PublishEnergyWasteAlert",
      "Effect": "Allow",
      "Action": [
        "sns:Publish"
      ],
      "Resource": "arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic"
    }
  ]
}