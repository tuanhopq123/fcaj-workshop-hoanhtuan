---
title: "Nhật ký công việc Tuần 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2

- Nghiên cứu Rubric và yêu cầu của đồ án cuối khóa.
- Phân tích yêu cầu hệ thống và thiết kế kiến trúc tổng thể.
- Hoàn thiện Proposal song ngữ.
- Xác định các dịch vụ AWS sẽ sử dụng cho dự án Smart Home Energy Waste Monitoring & Alert System.

---

### Công việc thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|------|-----------|--------------|-----------------|-------------------|
| 2 | Nghiên cứu Rubric và tiêu chí đánh giá của dự án. | 18/08/2025 | 18/08/2025 | AWS Study Group |
| 3 | Phân tích yêu cầu và lựa chọn các dịch vụ AWS phù hợp. | 19/08/2025 | 19/08/2025 | AWS Documentation |
| 4 | Thiết kế sơ đồ kiến trúc Serverless cho hệ thống. | 20/08/2025 | 20/08/2025 | AWS Architecture Center |
| 5 | Hoàn thiện Proposal song ngữ Anh - Việt. | 21/08/2025 | 21/08/2025 | Project Guideline |
| 6 | Rà soát kiến trúc và chuẩn bị cho giai đoạn triển khai. | 22/08/2025 | 22/08/2025 | AWS Well-Architected Framework |

---

### Kết quả đạt được

Trong tuần này, em đã hoàn thiện định hướng của đồ án và xây dựng kiến trúc tổng thể cho hệ thống.

Đề tài được lựa chọn là:

**Smart Home Energy Waste Monitoring & Alert System using Virtual Sensors on AWS**

Hệ thống được xây dựng nhằm giám sát mức tiêu thụ điện trong nhà thông minh thông qua các cảm biến ảo. Dữ liệu được xử lý bởi các dịch vụ Serverless của AWS để phát hiện những trường hợp sử dụng điện không hợp lý và tự động đưa ra cảnh báo khi phát hiện lãng phí điện năng.

Kiến trúc của hệ thống được thiết kế theo mô hình Serverless nhằm đảm bảo khả năng mở rộng, tối ưu chi phí và giảm thiểu việc quản lý hạ tầng.

---

### Kiến trúc giải pháp

Kiến trúc hệ thống sử dụng các dịch vụ AWS sau:

- Amazon API Gateway
- AWS Lambda
- Amazon DynamoDB
- Amazon S3
- Amazon CloudWatch
- AWS IAM

Luồng hoạt động của hệ thống gồm:

1. Cảm biến ảo tạo dữ liệu về phòng và thiết bị.
2. Request được gửi đến Amazon API Gateway.
3. AWS Lambda xử lý nghiệp vụ.
4. Dữ liệu được lưu trong Amazon DynamoDB.
5. Nhật ký và chỉ số được theo dõi bằng Amazon CloudWatch.
6. Các tài nguyên tĩnh và báo cáo được lưu trên Amazon S3.
7. AWS IAM quản lý quyền truy cập theo nguyên tắc Least Privilege.

### Sơ đồ kiến trúc ban đầu

Trong tuần này, em đã hoàn thành phiên bản đầu tiên của sơ đồ kiến trúc hệ thống.

![Sơ đồ kiến trúc hệ thống](/images/1-worklog/1.2-system-architecture.png)

---

### Tiến độ dự án

Đã hoàn thiện Proposal song ngữ bao gồm:

- Tổng quan dự án.
- Mục tiêu.
- Bài toán cần giải quyết.
- Kiến trúc hệ thống.
- Các dịch vụ AWS sử dụng.
- Luồng hoạt động.
- Kết quả mong đợi.

Bên cạnh đó, em cũng phân tích phương án kiểm thử và các rủi ro có thể gặp trong quá trình triển khai để chuẩn bị cho các tuần tiếp theo.

---

### Kiến thức thu nhận được

Sau tuần làm việc này, em đã hiểu rõ hơn về:

- Thiết kế kiến trúc Serverless trên AWS.
- Cách lựa chọn dịch vụ AWS phù hợp cho hệ thống IoT mô phỏng.
- Tối ưu chi phí theo mô hình Pay-as-you-go.
- Áp dụng AWS Well-Architected Framework vào thiết kế hệ thống.
- Xây dựng hệ thống Cloud có khả năng mở rộng và dễ bảo trì.

---

### Tổng kết Tuần 2

- Hoàn thành Proposal của dự án.
- Hoàn thiện sơ đồ kiến trúc đầu tiên.
- Lựa chọn sáu dịch vụ AWS cốt lõi.
- Xây dựng luồng hoạt động tổng thể.
- Chuẩn bị đầy đủ cho giai đoạn triển khai ở các tuần tiếp theo.

---

### Kế hoạch Tuần tiếp theo

- Cấu hình IAM Role và IAM Policy.
- Khởi tạo bảng Amazon DynamoDB.
- Thiết kế cấu trúc cơ sở dữ liệu.
- Chuẩn bị dữ liệu mẫu để kiểm thử.
- Bắt đầu triển khai các chức năng Backend bằng AWS Lambda.