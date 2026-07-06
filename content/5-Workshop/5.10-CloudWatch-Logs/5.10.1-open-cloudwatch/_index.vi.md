---
title : "Mở CloudWatch Logs"
date : 2026-07-05
weight : 1
chapter : false
pre : " <b> 5.10.1 </b> "
---

1. Kiểm tra Region góc trên bên phải: **Asia Pacific (Singapore) ap-southeast-1**.
2. Tại thanh tìm kiếm AWS Console, nhập: `CloudWatch`.
3. Chọn: **Amazon CloudWatch**.
4. Trong menu bên trái, tìm: **Logs**[cite: 13].
5. Chọn một trong hai tên tùy giao diện: **Log groups** hoặc **Log Management**[cite: 13].
6. Tại ô tìm kiếm log group, nhập: `energy-`[cite: 13].
7. Bạn phải thấy ít nhất hai log group[cite: 13]:
   * `/aws/lambda/energy-virtual-sensor`[cite: 13].
   * `/aws/lambda/energy-waste-detector`[cite: 13].

![CloudWatch Logs](/images/5-Workshop/5.10-CloudWatch/01-cloudwatch-log-groups.png)