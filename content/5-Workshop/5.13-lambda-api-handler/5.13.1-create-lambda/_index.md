---
title : "Create Lambda API Handler"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.13.1. </b> "
---

#### Step 1: Open Lambda Console

1. Check the Region in the top right corner: `Asia Pacific (Singapore) ap-southeast-1`
2. In the AWS Console search bar, enter: `Lambda`
3. Select the **Lambda** service.
4. In the left menu, select: **Functions**
5. Click **Create function**.

#### Step 2: Configure Function Details

- Select: **Author from scratch**
- Enter the following details:
  - **Function name**: `energy-api-handler`
  - **Runtime**: `Python 3.14`
- Keep the default configurations:
  - Durable execution: **Off**
  - EC2 capacity provider: **Off**
  - ARM64 architecture: **Off**
  - Custom execution role: **Off** *(AWS will create a basic execution role automatically)*.
  - Function URL: **Off**
  - VPC: **Off**
- Click **Create function**.

![Create Lambda API Handler](/images/5-Workshop/5.13-lambda-api-handler/5.13.1-create-lambda.png)