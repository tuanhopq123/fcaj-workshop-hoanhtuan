---
title : "Xóa AWS IoT Rule"
date : 2026-07-05 
weight : 6
chapter : false
pre : " <b> 5.18.6 </b> "
---

Phải xóa IoT Rule trước khi xóa Lambda Waste Detector để tránh giữ một Rule trỏ đến Lambda không còn tồn tại.

1. **Mở AWS IoT Core**
   * Tìm kiếm và mở **AWS IoT Core**.
   * Trong menu bên trái, chọn **Message routing** -> **Rules**.

2. **Xóa Rule**
   * Chọn Rule `iot_rule_energy_telemetry_to_waste_detector`.
   * Chọn **Delete**, nhập xác nhận và kiểm tra Rule đã biến mất khỏi danh sách.

![Xóa Rule 1](/images/5-Workshop/5.18-CleanUp/Xoa-Rule.png)
![Xóa Rule 2](/images/5-Workshop/5.18-CleanUp/Xoa-Rule2.png)