---
title : "Verify API Gateway Permissions on Lambda"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b> 5.13.9. </b> "
---

#### Execution Steps

1. Navigate to: **Lambda** -> `energy-api-handler` -> **Configuration** -> **Permissions**.
2. Locate the **Resource-based policy statements** section.
3. You should see a statement with content similar to the following:
   - **Principal**: `apigateway.amazonaws.com`
   - **Action**: `lambda:InvokeFunction`
   - **Source ARN**: `arn:aws:execute-api:ap-southeast-1:347685737655:<API-ID>/*`

*Note: Do not manually edit this policy if the API Gateway Console has already successfully created it.*

![Verify Resource-based Policy](/images/5-Workshop/5.13-lambda-api-handler/5.13.9-resource-policy.png)