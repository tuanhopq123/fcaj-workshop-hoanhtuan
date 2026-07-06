---
title : "Adjust Timeout"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.13.2. </b> "
---

Since the Lambda function will execute Query or Scan operations on DynamoDB, we need to increase the default timeout to 10 seconds.

#### Execution Steps

1. In the `energy-api-handler` Lambda function, select the **Configuration** tab.
2. Select **General configuration** from the left menu.
3. Click **Edit**.
4. Keep **Memory**: `128 MB`
5. Set **Timeout**: `0 min 10 sec`
6. Click **Save**.

*Note: There is no need to increase the memory configuration at this stage.*

![Adjust Timeout](/images/5-Workshop/5.13-lambda-api-handler/5.13.2-adjust-timeout.png)