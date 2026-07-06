---
title: "5.7. Tạo Cảm biến Ảo bằng Lambda"
date: 2026-07-05
weight: 7
chapter: true
description: "Tổng quan và điều hướng cấu trúc để xây dựng cảm biến ảo bằng Lambda nhằm giả lập dữ liệu tiêu thụ điện năng IoT."
---

Cảm biến ảo bằng Lambda (Lambda Virtual Sensor) chịu trách nhiệm giả lập dữ liệu tiêu thụ điện năng thực tế từ các thiết bị phòng thí nghiệm và đẩy các gói dữ liệu đo lường này trực tiếp đến AWS IoT Core.

Trong phần này, bạn sẽ trải qua các bước sau để xây dựng và kiểm thử cảm biến ảo:

#### 1. [5.7.1 Tạo Hàm Lambda](5.7.1-create-function.md)
Khởi tạo môi trường hàm cốt lõi trên AWS Lambda sử dụng môi trường thực thi runtime Python.

#### 2. [5.7.2 Cấu hình Biến môi trường](5.7.2-environment-variables/)
Thiết lập các cấu hình động và các cặp key-value tách biệt để tối ưu hóa việc tham chiếu tài nguyên một cách linh hoạt.

#### 3. [5.7.3 Cấp quyền IAM](5.7.3-iam-permissions/)
Chỉnh sửa chính sách của vai trò thực thi để cho phép hàm gửi dữ liệu đo lường an toàn đến AWS IoT Core.

#### 4. [5.7.4 Triển khai Mã nguồn Giả lập](5.7.4-deploy-code/)
Cài đặt và triển khai đoạn mã Python giả lập cốt lõi giúp tạo ra các thông số thiết bị sát với thực tế.

#### 5. [5.7.5 Tạo Sự kiện Kiểm thử](5.7.5-create-test-event/)
Định nghĩa các gói dữ liệu JSON cấu hình tùy chỉnh để phục vụ cho việc chạy thử nghiệm thủ công.

#### 6. [5.7.6 Thực thi Kiểm thử và Xác minh Kết quả](5.7.6-execute-test/)
Kích hoạt chạy thử nghiệm để kiểm tra hoạt động toàn diện của hệ thống và đánh giá các bản ghi logs đầu ra thời gian thực.