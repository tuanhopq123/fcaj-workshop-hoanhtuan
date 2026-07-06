---
title: "5.6.1 Create function"
weight: 1
---

# 5.6.1 Create AWS Lambda Function

To start processing our IoT ecosystem's telemetry stream, we need to initialize a serverless compute function using AWS Lambda.

### Step-by-Step Instructions:

1. On the **AWS Management Console**, type `Lambda` into the top search bar.
2. Select the **Lambda** service from the search results.
3. In the left navigation menu, click on **Functions**.
4. Click the **Create function** button at the top right.
5. On the **Create function** screen, configure the following settings:
   * Select **Author from scratch**.
   * **Function name:** `energy-waste-detector`
   * **Runtime:** Select `Python 3.14`.
6. Click the **Create function** button at the bottom to initialize your workspace.