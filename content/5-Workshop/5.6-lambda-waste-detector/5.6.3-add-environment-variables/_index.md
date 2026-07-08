---
title : "Add Environment Variables"
date : 2026-07-01
weight : 3
chapter : false
pre : " <b> 5.6.3 </b> "
---

1. **Open Environment variables**
   * On the `energy-waste-detector` Lambda page, go to the **Configuration** tab.
   * On the left, select **Environment variables**.
   * Click **Edit**.

2. **Add the following 3 variables**

```
DDB_TABLE = EnergyWasteData
SNS_TOPIC_ARN = arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic
POWER_THRESHOLD_W = 120
```

3. **Save**
   * Click **Save**.

![Environment variables configured](/images/5-Workshop/5.6-lambda/pic4.png)
