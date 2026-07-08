---
title : "Thêm Environment Variables"
date : 2026-07-01
weight : 3
chapter : false
pre : " <b> 5.6.3 </b> "
---

1. **Mở Environment variables**
   * Trong trang Lambda `energy-waste-detector`, vào tab **Configuration**.
   * Chọn bên trái **Environment variables**.
   * Bấm **Edit**.

2. **Thêm 3 biến sau**

```
DDB_TABLE = EnergyWasteData
SNS_TOPIC_ARN = arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic
POWER_THRESHOLD_W = 120
```

3. **Lưu lại**
   * Bấm **Save**.

![Environment variables đã cấu hình](/images/5-Workshop/5.6-lambda/pic4.png)
