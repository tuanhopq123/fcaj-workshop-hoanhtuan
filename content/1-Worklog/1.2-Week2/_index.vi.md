---
title: "Nhật ký công việc Tuần 2"
date: 2026-04-24
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

| Ngày | Công việc                                                                                                                        | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo             |
| ---- | -------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------------------ |
| 1    | Nghiên cứu yêu cầu Workshop, Rubric đánh giá và tài liệu hướng dẫn của chương trình AWS Workforce Bootcamp.                      | 24/04/2026   | 24/04/2026      | AWS Study Group                |
| 2    | Phân tích yêu cầu của hệ thống và lựa chọn các dịch vụ AWS phù hợp cho đề tài Smart Home Energy Waste Monitoring & Alert System. | 25/04/2026   | 25/04/2026      | AWS Documentation              |
| 3    | Thiết kế phiên bản đầu tiên của kiến trúc Serverless và xây dựng luồng hoạt động tổng thể của hệ thống.                          | 26/04/2026   | 27/04/2026      | AWS Architecture Center        |
| 4    | Hoàn thiện Proposal song ngữ, bao gồm mục tiêu, kiến trúc hệ thống, kết quả mong đợi và lộ trình triển khai.                     | 28/04/2026   | 29/04/2026      | Project Guideline              |
| 5    | Rà soát và tối ưu kiến trúc theo AWS Well-Architected Framework trước khi bắt đầu giai đoạn triển khai.                          | 30/04/2026   | 30/04/2026      | AWS Well-Architected Framework |


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
- Chuẩn bị đầy đủ tài liệu kỹ thuật trước khi bước vào giai đoạn triển khai.

---

### Kế hoạch Tuần tiếp theo

- Cấu hình AWS IAM User, Role và Policy.
- Khởi tạo bảng Amazon DynamoDB.
- Thiết kế cấu trúc cơ sở dữ liệu.
- Chuẩn bị dữ liệu mẫu phục vụ kiểm thử.
- Bắt đầu triển khai các dịch vụ AWS đầu tiên của Workshop.