---
title: "Nhật ký công việc Tuần 6"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---


## Mục tiêu Tuần 6

* Tích hợp hệ thống giám sát và ghi log tập trung cho ứng dụng.
* Kiểm thử toàn bộ luồng xử lý của hệ thống theo mô hình Serverless.
* Hoàn thành các bài thực hành về AWS Security Hub, AWS Lambda và quản lý tài nguyên bằng Tags.

---

## Công việc thực hiện trong tuần

| Nội dung | Kết quả |
|----------|----------|
| Amazon CloudWatch | Tích hợp CloudWatch để thu thập log từ AWS Lambda và API Gateway. Thiết lập Metric Filters và CloudWatch Alarms nhằm theo dõi lỗi hệ thống và gửi cảnh báo qua Amazon SNS khi phát hiện bất thường. |
| Kiểm thử hệ thống | Thực hiện kiểm thử End-to-End bằng Postman để xác minh các API xử lý dữ liệu cảm biến, cảnh báo lãng phí điện và truy xuất báo cáo. Đồng thời đối chiếu dữ liệu trên DynamoDB với log trong CloudWatch để đảm bảo hệ thống hoạt động chính xác. |
| Lab 18 - AWS Security Hub | Thực hành kích hoạt và cấu hình AWS Security Hub nhằm đánh giá mức độ bảo mật của tài khoản AWS theo các tiêu chuẩn bảo mật phổ biến như AWS Foundational Security Best Practices và CIS Benchmark. |
| Lab 22 - Optimizing EC2 Costs with Lambda | Xây dựng giải pháp tự động bật và tắt EC2 theo lịch bằng AWS Lambda kết hợp IAM Role nhằm tối ưu chi phí vận hành và nâng cao hiệu quả quản lý tài nguyên. |
| Lab 27 - Resource Tags & Resource Groups | Thực hành gán Tags cho tài nguyên AWS và sử dụng Resource Groups để tổ chức, quản lý và tự động hóa các tài nguyên theo từng môi trường hoặc dự án. |

---

## Kết quả đạt được

* Hoàn thành việc tích hợp Amazon CloudWatch vào hệ thống Serverless.
* Thiết lập thành công cơ chế theo dõi log, giám sát lỗi và cảnh báo tự động.
* Kiểm thử thành công toàn bộ luồng xử lý từ API Gateway đến AWS Lambda và DynamoDB.
* Hiểu rõ hơn về các giải pháp bảo mật tập trung thông qua AWS Security Hub.
* Nâng cao kiến thức về tối ưu chi phí bằng AWS Lambda và quản lý tài nguyên thông qua Tags.

---

## Đánh giá

* Hoàn thành 100% mục tiêu của tuần.
* Hệ thống Smart Home Energy Waste Monitoring đã có khả năng giám sát và theo dõi hoạt động theo thời gian thực.
* Kiến thức từ các bài Lab giúp nâng cao tư duy thiết kế hệ thống Cloud theo các nguyên tắc bảo mật, khả năng quan sát (Observability) và tối ưu chi phí.

---

## Kế hoạch tuần tiếp theo

* Hoàn thiện tài liệu hướng dẫn triển khai hệ thống.
* Xây dựng quy trình triển khai và dọn dẹp tài nguyên trên AWS.
* Tiếp tục hoàn thành các bài thực hành AWS theo lộ trình đào tạo.