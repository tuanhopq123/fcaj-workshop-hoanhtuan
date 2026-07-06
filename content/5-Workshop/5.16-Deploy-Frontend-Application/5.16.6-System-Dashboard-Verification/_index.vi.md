---
title : "Kiểm tra và Xác thực Hệ thống trên Dashboard"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.16.6. </b> "
---

#### Bước 1: Đăng nhập vào Ứng dụng

1. Nhập thông tin tài khoản hợp lệ đã được xác thực thông qua Amazon Cognito User Pool (Email và mật khẩu đã đăng ký).
2. Nhấn nút **Sign in**.

#### Bước 2: Kiểm tra dữ liệu Giám sát Điện năng Thực tế

1. Sau khi xác thực thành công, hệ thống sẽ tự động chuyển hướng bạn vào giao diện Dashboard chính.
2. Xác nhận thanh điều hướng phía trên hiển thị đúng thông tin ngữ cảnh người dùng hiện tại (`Cognito authenticated`).
3. Kiểm tra xem **Energy Monitoring Dashboard** có kích hoạt các API truy vấn thành công để lấy về dữ liệu số liệu thực tế từ database hay không:
   - **Rooms:** Số lượng phòng Smart Home Lab đã cấu hình.
   - **Telemetry:** Tổng số mẫu dữ liệu đo lường nhận được gần nhất.
   - **Alerts:** Số lượng cảnh báo lãng phí điện năng đang kích hoạt.
   - **Reports:** Tổng số báo cáo dữ liệu đã được hệ thống khởi tạo.
4. Kiểm tra bảng **Telemetry gần nhất** xem dữ liệu có cập nhật động các dòng nhật ký theo thời gian thực hay không, bao gồm: Thời gian (Timestamp), Tên thiết bị (`Air Conditioner`), Công suất tiêu thụ (`W`), Trạng thái thiết bị, Trạng thái có người trong phòng, và Kết quả phân tích lãng phí điện năng.

![Giao diện Dashboard](/images/5-Workshop/5.16/WED1.png)