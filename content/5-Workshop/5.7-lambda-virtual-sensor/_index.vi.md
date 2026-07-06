---
title: "5.7. Tạo Lambda Virtual Sensor"
date: 2026-07-05
weight: 7
chapter: true
---

# 5.7. Tạo Lambda Virtual Sensor

Lambda Virtual Sensor có nhiệm vụ mô phỏng dữ liệu tiêu thụ điện thực tế của thiết bị trong phòng lab và gửi trực tiếp các payload này đến AWS IoT Core.

Trong mục này, bạn sẽ thực hiện các bước sau để khởi tạo và kiểm thử cảm biến ảo:
1. **Khởi tạo Hàm Lambda**: Tạo hàm cơ bản sử dụng môi trường Python.
2. **Cấu hình Biến Môi Trường**: Thiết lập các giá trị động cho mã nguồn linh hoạt.
3. **Cấp Quyền IAM**: Cho phép hàm gửi dữ liệu đến AWS IoT Core.
4. **Triển khai Mã Nguồn Mô Phỏng**: Viết và deploy script giả lập Python.
5. **Khởi Tạo Sự Kiện Kiểm Thử**: Định nghĩa cấu hình test manual.
6. **Thực Thi Thử Nghiệm Và Kiểm Tra**: Đánh giá kết quả đầu ra và log hệ thống.