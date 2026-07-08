---
title : "Kiểm tra dữ liệu tự động"
date : 2026-07-05
weight : 4
chapter : false
pre : " <b> 5.9.4 </b> "
---

Sau khi schedule được tạo, chờ khoảng **2–3 phút**. Trong thời gian này, không bấm Test thủ công trên Lambda.

#### Kiểm tra DynamoDB
1. Mở tab AWS Console mới và tìm **DynamoDB**.
2. Chọn **Tables** -> chọn bảng `EnergyWasteData`.
3. Chọn **Explore table items** -> Bấm **Run** (hoặc Scan).
4. Sắp xếp hoặc tìm các item mới có:
   * `PK = ROOM#lab-01`
   * `SK` bắt đầu bằng `TELEMETRY#`
5. Mở một item mới nhất và kiểm tra:
   * `sensorId = virtual-sensor-01`
   * `source = eventbridge-scheduler`

Kết quả đúng là sau vài phút phải có nhiều item mới được tạo tự động với các timestamp khác nhau.

![Verify Data](/images/5-Workshop/5.9-EventBridge/04-du-lieu-telemetry-tu-dong.png)