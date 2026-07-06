---
title : "Chọn Lambda Target"
date : 2026-07-05
weight : 3
chapter : false
pre : " <b> 5.9.3 </b> "
---

1. **Chọn loại Target**
   + Tại **Target API**, chọn: **Templated targets**
   + Tìm và chọn: **AWS Lambda Invoke**

2. **Chọn Lambda Function**
   + Tại **Lambda function**, chọn: `energy-virtual-sensor`
   + *Cẩn thận không chọn nhầm `energy-waste-detector`.*

3. **Nhập Payload**
   + Xóa nội dung mẫu và dán mã JSON sau:

    {
      "source": "eventbridge-scheduler",
      "forceWaste": false
    }

   + Bấm: **Next**

4. **Cấu hình Schedule Settings**
   + **Enable schedule**: Enable
   + **Retry policy**: Retry Off
   + **Dead-letter queue (DLQ)**: None
   + **Encryption**: Use AWS owned key
   + **Permissions**: Create new role for this schedule
   + **Role name**: `eventbridge-scheduler-energy-virtual-sensor-role`
   + Bấm: **Next**

5. **Review and Create**
   + Kiểm tra lại cấu hình và bấm: **Create schedule**

![Target](/images/5-Workshop/5.9-EventBridge/03-schedule-enabled.png)