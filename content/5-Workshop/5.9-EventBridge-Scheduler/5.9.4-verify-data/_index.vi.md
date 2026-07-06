---
title : "Kiểm tra dữ liệu tự động"
date : 2026-07-05
weight : 4
chapter : false
pre : " <b> 5.9.4 </b> "
---

Sau khi schedule được tạo, chờ khoảng **2–3 phút**[cite: 12]. Trong thời gian này, không bấm Test thủ công trên Lambda[cite: 12].

#### Kiểm tra DynamoDB
1. Mở tab AWS Console mới và tìm **DynamoDB**[cite: 12].
2. Chọn **Tables** -> chọn bảng `EnergyWasteData`[cite: 12].
3. Chọn **Explore table items** -> Bấm **Run** (hoặc Scan)[cite: 12].
4. Sắp xếp hoặc tìm các item mới có[cite: 12]:
   * `PK = ROOM#lab-01`
   * `SK` bắt đầu bằng `TELEMETRY#`
5. Mở một item mới nhất và kiểm tra[cite: 12]:
   * `sensorId = virtual-sensor-01`
   * `source = eventbridge-scheduler`

Kết quả đúng là sau vài phút phải có nhiều item mới được tạo tự động với các timestamp khác nhau[cite: 12].

![Verify Data](/images/5-Workshop/5.9-EventBridge/04-du-lieu-telemetry-tu-dong.png)