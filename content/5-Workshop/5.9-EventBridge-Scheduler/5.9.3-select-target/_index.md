---
title : "Select Lambda Target"
date : 2026-07-05 
weight : 3
chapter : false
pre : " <b> 5.9.3 </b> "
---

1. **Select Target API**
   + Under **Target API**, choose: **Templated targets**
   + Find and choose: **AWS Lambda Invoke**

2. **Choose Lambda Function**
   + For **Lambda function**, choose: `energy-virtual-sensor`
   + *Warning: Do not choose `energy-waste-detector`.*

3. **Input Payload**
   + Delete the sample content and paste the following JSON:

    {
      "source": "eventbridge-scheduler",
      "forceWaste": false
    }

   + Click: **Next**

4. **Schedule Settings**
   + **Enable schedule**: Enable
   + **Retry policy**: Retry Off
   + **Dead-letter queue (DLQ)**: None
   + **Encryption**: Use AWS owned key
   + **Permissions**: Create new role for this schedule
   + **Role name**: `eventbridge-scheduler-energy-virtual-sensor-role`
   + Click: **Next**

5. **Review and Create**
   + Review the configuration and click: **Create schedule**

![Target](/images/5-Workshop/5.9-EventBridge/03-schedule-enabled.png)