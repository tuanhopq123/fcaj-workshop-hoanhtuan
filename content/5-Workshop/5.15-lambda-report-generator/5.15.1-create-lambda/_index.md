---
title : "Create Lambda Function"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.15.1. </b> "
---

#### Step 1: Open Lambda Console

1. Check the Region in the top right corner:
   - **Asia Pacific (Singapore)**
   - `ap-southeast-1`
2. In the AWS Console search bar, enter: `Lambda`
3. Select the **Lambda** service.
4. In the left navigation pane, choose **Functions**.
5. Click **Create function**.

![Open Lambda](/images/5-Workshop/5.15-lambda-report/5.15.1-step1.png)

#### Step 2: Configure Lambda Details

1. On the Create function page, select **Author from scratch**.
2. For **Function name**, enter: `energy-report-generator`
3. For **Runtime**, select: `Python 3.14`
4. For **Architecture**, keep: `x86_64`
5. Keep the following default settings:
   - Durable execution: **Off**
   - EC2 capacity provider: **Off**
   - ARM64 architecture: **Off**
   - Custom execution role: **Off** (AWS will automatically create a new execution role with basic Lambda permissions).
   - Function URL: **Off**
   - VPC: **Off**
6. Click **Create function**.

![Configure Lambda](/images/5-Workshop/5.15-lambda-report/5.15.1-step2.png)