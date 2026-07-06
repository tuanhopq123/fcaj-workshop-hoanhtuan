---
title : "Create Lambda Integration in API Gateway"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.13.7. </b> "
---

Now, we will connect the **API Gateway** to the `energy-api-handler` Lambda function.

#### Step 1: Open Integrations

1. Navigate to: **API Gateway** -> **APIs** -> `energy-waste-http-api`
2. In the left menu, select: **Develop** -> **Integrations**
3. Locate **Manage integrations**.
4. Click **Create** (or **Create and attach an integration**).

#### Step 2: Configure Lambda Integration

1. For **Integration type**, select: **Lambda function**
2. For **AWS Region**, select: `ap-southeast-1`
3. For **Lambda function**, select: `energy-api-handler`
4. For **Payload format version**, select: `2.0`
5. If an **Integration name** is required, enter: `energy-api-handler-integration`
6. Keep the timeout as default.
7. Click **Create** (or **Create integration**).

![Create Lambda Integration](/images/5-Workshop/5.13-lambda-api-handler/5.13.7-create-integration.png)