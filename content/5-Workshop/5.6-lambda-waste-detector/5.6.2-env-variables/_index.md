---
title: "5.6.2 Env variables"
weight: 1
---

# 5.6.2 Configure Environment Variables

Instead of hardcoding system values like table names or topic ARNs, we will leverage environment variables within our Lambda function to ensure modular configuration.

### Step-by-Step Instructions:

1. Navigate to the detail dashboard of your newly created **energy-waste-detector** function.
2. Click on the **Configuration** tab in the main tab menu.
3. From the left-side sub-menu, select **Environment variables**.
4. Click the **Edit** button on the right.
5. Click **Add environment variable** and fill in the following 3 key-value pairs exactly:
   * **Key:** `DDB_TABLE` | **Value:** `EnergyWasteData`
   * **Key:** `SNS_TOPIC_ARN` | **Value:** `arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic`
   * **Key:** `POWER_THRESHOLD_W` | **Value:** `120`
6. Click the **Save** button to apply the environment configuration.