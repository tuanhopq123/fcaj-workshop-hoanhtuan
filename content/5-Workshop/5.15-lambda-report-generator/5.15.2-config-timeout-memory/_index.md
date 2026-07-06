---
title : "Configure Timeout and Memory"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.15.2. </b> "
---

Because the report needs to read multiple DynamoDB items, aggregate data, and generate a JSON file, we need to increase the default resources:
- **Memory**: 256 MB
- **Timeout**: 30 seconds

#### Step 1: Open General Configuration

1. In your `energy-report-generator` Lambda function.
2. Select the **Configuration** tab.
3. In the left menu, choose **General configuration**.
4. Click **Edit**.

![Open General Config](/images/5-Workshop/5.15-lambda-report/5.15.2-step1.png)

#### Step 2: Enter Configuration Details

1. For **Memory**, enter: `256 MB`
2. For **Timeout**, enter: `0 min 30 sec`
3. Keep **Ephemeral storage**: `512 MB`
4. Click **Save**.

![Edit Configuration](/images/5-Workshop/5.15-lambda-report/5.15.2-step2.png)

*Note: Verify that the settings are correctly applied (Memory: 256 MB, Timeout: 0 min 30 sec, Ephemeral storage: 512 MB). You don't need a separate screenshot if this information is visible after saving.*