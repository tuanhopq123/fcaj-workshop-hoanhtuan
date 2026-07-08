---
title : "Kiểm tra DynamoDB"
date : 2026-07-05
weight : 4
chapter : false
pre : " <b> 5.10.4 </b> "
---

Bước này dùng để đối chiếu log với dữ liệu thực tế.

1. Mở tab AWS Console mới.
2. Tìm: **DynamoDB**.
3. Chọn: **Tables** -> chọn bảng `EnergyWasteData`.
4. Chọn: **Explore table items** -> Bấm **Run** (hoặc Scan).
5. Tìm các item có `PK = ROOM#lab-01`.
6. Kiểm tra có các loại sort key: `PROFILE`, `TELEMETRY#...`, `ALERT#...`.
7. **Dữ liệu Telemetry**:
   * Mở một item mới được tạo và kiểm tra: `sensorId = virtual-sensor-01`, `roomId = lab-01`, `deviceStatus = ON hoặc OFF`, và `source = eventbridge-scheduler`.
8. **Dữ liệu Alert** (nếu có):
   * Mở một item `ALERT#...` và kiểm tra: `roomId = lab-01`, `deviceStatus = ON`, `occupancy = false`, `powerW >= 120`.

![DynamoDB Verification](/images/5-Workshop/5.10-CloudWatch/04-dynamodb-core-result.png)