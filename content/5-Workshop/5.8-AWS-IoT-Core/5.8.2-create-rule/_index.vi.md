---
title : "Tạo IoT Rule"
date : 2026-07-05 
weight : 2
chapter : false
pre : " <b> 5.8.2 </b> "
---

1. Tại **Rule name**, nhập chính xác: `iot_rule_energy_telemetry_to_waste_detector` *(Không thêm dấu cách và không đổi thành dấu gạch ngang).*
2. Tại **Rule description**, nhập: `Forward energy telemetry from MQTT topic to Lambda Waste Detector`
3. Phần **Tags** có thể để trống. Bấm: **Next**
4. Trang tiếp theo thường có tên: **Configure SQL statement**
5. Tại **SQL version**, chọn: `2016-03-23` *(Đây cũng là phiên bản mà AWS IoT Console thường chọn mặc định).*
6. Tại ô **SQL statement**, xóa nội dung mẫu rồi dán:
```sql
SELECT * FROM 'home/lab/telemetry'