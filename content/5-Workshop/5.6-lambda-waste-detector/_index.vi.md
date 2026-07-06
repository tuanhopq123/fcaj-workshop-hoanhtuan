---
title: "5.6 Cấu hình AWS Lambda và Kiểm thử Hệ thống"
weight: 6
value: 56
description: "Tổng quan về việc triển khai AWS Lambda để xử lý dữ liệu đo lường IoT và thực hiện kiểm thử tích hợp toàn diện."
---

Trong phần này, chúng ta sẽ tìm hiểu và triển khai **AWS Lambda** để kết nối dữ liệu thu thập từ IoT Core với các dịch vụ phân tích và xử lý thông báo phía sau. AWS Lambda đóng vai trò là một dịch vụ tính toán phi máy chủ (serverless) hoạt động theo kiến trúc hướng sự kiện, tự động xử lý các gói dữ liệu theo nhu cầu thực tế.

### Mục tiêu bài học
* **Khởi tạo tính toán phi máy chủ:** Triển khai môi trường hàm AWS Lambda độc lập dựa trên ngôn ngữ Python.
* **Cô lập biến quản lý trạng thái:** Bảo mật thông tin cấu hình hệ thống bằng cách sử dụng Biến môi trường (Environment Variables) của Lambda.
* **Kiểm soát quyền truy cập IAM:** Áp dụng các chính sách bảo mật để cấp quyền tương tác đọc/ghi dữ liệu với Amazon DynamoDB và Amazon SNS.
* **Kiểm thử tích hợp hệ thống toàn diện:** Kích hoạt các gói dữ liệu giả lập sự kiện lãng phí điện năng, tiến hành kiểm tra bảng dữ liệu thực tế và các kênh nhận thông báo thời gian thực.

---

### Cấu trúc chương học

#### 1. [5.6.1 Tạo Hàm AWS Lambda](5.6.1-create-function/)
Hướng dẫn từng bước để khởi tạo môi trường thực thi runtime Python bên trong giao diện AWS Lambda console.

#### 2. [5.6.2 Cấu hình Biến môi trường](5.6.2-env-variables/)
Hướng dẫn thiết lập các cấu hình key-value tách biệt nhằm lưu trữ an toàn các tham chiếu đến tài nguyên AWS đích.

#### 3. [5.6.3 Cấu hình Quyền thực thi IAM](5.6.3-iam-permissions/)
Chỉnh sửa IAM execution role của Lambda để cấp quyền ghi dữ liệu một cách an toàn vào Amazon DynamoDB và Amazon SNS.

#### 4. [5.6.4 Triển khai Mã nguồn và Xác minh Kết quả](5.6.4-deploy-test/)
Triển khai đoạn mã xử lý logic hoàn chỉnh, kích hoạt thử nghiệm các gói dữ liệu giả lập lỗi và kiểm tra kết quả đầu ra của hệ thống.