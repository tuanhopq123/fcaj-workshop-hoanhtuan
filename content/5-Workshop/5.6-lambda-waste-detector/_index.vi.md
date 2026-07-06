# 5.6 Cấu hình AWS Lambda và Kiểm thử Hệ thống

### Tổng quan
Trong chương này, chúng ta sẽ tìm hiểu và triển khai dịch vụ **AWS Lambda** nhằm thiết lập cầu nối xử lý logic giữa luồng dữ liệu telemetry thu thập từ IoT Core với các hệ thống phân tích và thông báo đầu ra. AWS Lambda đóng vai trò là một dịch vụ tính toán hướng sự kiện (serverless), tự động thực thi mã nguồn để xử lý các gói tin khi có yêu cầu.

### Mục tiêu bài học
* **Khởi tạo tính toán Serverless:** Triển khai môi trường thực thi độc lập cho hàm xử lý AWS Lambda dựa trên ngôn ngữ Python.
* **Tách biệt cấu hình bằng biến môi trường:** Bảo mật các thông số cấu hình hệ thống quan trọng thông qua việc thiết lập Lambda Environment Variables.
* **Quản trị phân quyền bảo mật IAM:** Áp dụng chính sách bảo mật nội bộ để cấp đặc quyền ghi/đọc dữ liệu an toàn với Amazon DynamoDB và Amazon SNS.
* **Kiểm thử tích hợp toàn diện hệ thống:** Kích hoạt thử nghiệm bằng các gói tin mô phỏng hành vi lãng phí điện năng, đồng thời kiểm tra tính đồng bộ của cơ sở dữ liệu và hệ thống gửi thông báo thời gian thực.

### Nội dung chi tiết
1. [5.6.1 Khởi tạo hàm AWS Lambda](5.6.1-create-function/)
2. [5.6.2 Cấu hình biến môi trường (Environment Variables)](5.6.2-env-variables/)
3. [5.6.3 Cấu hình phân quyền IAM cho Lambda](5.6.3-iam-permissions/)
4. [5.6.4 Triển khai mã nguồn và Kiểm thử hệ thống](5.6.4-deploy-test/)