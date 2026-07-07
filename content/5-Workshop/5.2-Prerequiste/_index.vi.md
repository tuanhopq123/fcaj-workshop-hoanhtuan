---
title : "Điều kiện chuẩn bị"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

# Điều kiện chuẩn bị

Trước khi bắt đầu Workshop, cần chuẩn bị tài khoản AWS và cấu hình môi trường làm việc để toàn bộ tài nguyên được triển khai đúng khu vực (Region).

Trong Workshop này, tất cả các dịch vụ AWS đều được triển khai tại **Asia Pacific (Singapore)**. Việc sử dụng cùng một Region giúp các dịch vụ có thể kết nối với nhau dễ dàng, giảm độ trễ, đồng thời tránh việc vô tình tạo tài nguyên ở nhiều Region khác nhau gây phát sinh chi phí không cần thiết.

Ngoài ra, việc thiết lập **Region mặc định** sẽ giúp toàn bộ các bước trong Workshop diễn ra thống nhất và hạn chế sai sót trong quá trình triển khai.

---

# Bước 5.2.1 - Chọn AWS Region

AWS cho phép người dùng lựa chọn Region thông qua thanh điều hướng ở phía trên AWS Management Console.

Các tài nguyên như Amazon EC2, Amazon S3, AWS Lambda, Amazon DynamoDB hay Amazon API Gateway đều được tạo theo từng Region riêng biệt. Vì vậy, trước khi triển khai Workshop, cần đảm bảo đang làm việc tại đúng Region được yêu cầu.

## Các bước thực hiện

1. Đăng nhập vào **AWS Management Console**.
2. Quan sát góc trên bên phải của giao diện.
3. Nhấp vào tên Region hiện tại.
4. Trong danh sách các Region, chọn:

```
Asia Pacific (Singapore)
```

5. Chờ AWS Console tải lại.
6. Kiểm tra góc trên bên phải hiển thị:

```
Singapore
```

hoặc

```
Asia Pacific (Singapore)
```

Hình dưới đây minh họa vị trí lựa chọn AWS Region.

![Select Region](/images/5-Workshop/5.2-Prerequisite/prerequisite1.png)

---

# Bước 5.2.2 - Thiết lập Region mặc định

Sau khi lựa chọn đúng Region, nên thiết lập **Singapore** làm Region mặc định cho tài khoản.

Việc này giúp AWS Console tự động sử dụng Region Singapore mỗi khi đăng nhập, hạn chế tối đa việc triển khai nhầm tài nguyên sang Region khác.

## Các bước thực hiện

1. Trên thanh điều hướng của AWS Console, chọn biểu tượng **Settings**.
2. Chọn **See all user settings**.
3. Tìm mục:

```
Localization and default Region
```

4. Chọn **Edit**.
5. Trong phần **Default Region**, chọn:

```
Asia Pacific (Singapore)
```

6. Lưu thay đổi.

Sau khi hoàn tất, mọi phiên làm việc mới sẽ tự động sử dụng Region Singapore làm Region mặc định.

Hình dưới đây minh họa giao diện thiết lập Region mặc định.

![Default Region](/images/5-Workshop/5.2-Prerequisite/prerequisite2.png)

---

# Kết quả

Sau khi hoàn thành bước này, môi trường AWS đã sẵn sàng để triển khai Workshop.

Tất cả các tài nguyên được tạo trong những phần tiếp theo sẽ nằm trong **Asia Pacific (Singapore)**, đảm bảo tính thống nhất của toàn bộ hệ thống và tránh phát sinh chi phí do triển khai sai Region.