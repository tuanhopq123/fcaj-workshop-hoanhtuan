---
title : "Điều chỉnh Timeout"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.13.2. </b> "
---

Do Lambda sẽ thực hiện các thao tác Query hoặc Scan dữ liệu trên DynamoDB, chúng ta cần tăng timeout từ mức mặc định lên 10 giây để đảm bảo chức năng chạy ổn định.

#### Thực hiện

1. Trong hàm Lambda `energy-api-handler`, chọn tab: **Configuration**
2. Chọn: **General configuration**
3. Bấm nút: **Edit**
4. Giữ nguyên **Memory**: `128 MB`
5. Đặt lại **Timeout**: `0 min 10 sec`
6. Bấm: **Save**

*Lưu ý: Chưa cần tăng dung lượng memory ở giai đoạn hiện tại.*

![Điều chỉnh Timeout](/images/5-Workshop/5.13-lambda-api-handler/5.13.2-adjust-timeout.png)