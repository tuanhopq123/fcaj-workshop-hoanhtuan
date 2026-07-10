---
title: "Nhật ký công việc Tuần 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---


## Mục tiêu Tuần 4

* Phát triển các hàm AWS Lambda để xử lý nghiệp vụ của hệ thống giám sát điện năng.
* Kết nối AWS Lambda với Amazon DynamoDB để lưu trữ và truy xuất dữ liệu.
* Nghiên cứu các giải pháp mạng nâng cao trên AWS thông qua các bài thực hành.

---

## Công việc thực hiện trong tuần

| Nội dung | Kết quả |
|----------|----------|
| Phát triển AWS Lambda | Xây dựng các hàm Lambda xử lý dữ liệu từ cảm biến ảo, truy vấn thông tin phòng, thiết bị và cảnh báo lãng phí điện. |
| Tích hợp Amazon DynamoDB | Kết nối Lambda với DynamoDB để đọc và ghi dữ liệu của hệ thống Smart Home Energy Monitoring. |
| Thiết kế kiến trúc xử lý | Hoàn thiện luồng xử lý Serverless giữa Lambda và DynamoDB, chuẩn bị cho việc tích hợp API Gateway ở tuần tiếp theo. |
| Lab 10 - Route 53 Hybrid DNS | Thực hành cấu hình Hybrid DNS với Route 53 Resolver, Inbound/Outbound Endpoints và Resolver Rules. |
| Lab 19 - VPC Peering & Network ACL | Thiết lập kết nối giữa nhiều VPC bằng VPC Peering, cấu hình Network ACL và Cross-Peering DNS. |
| Lab 20 - AWS Transit Gateway | Triển khai AWS Transit Gateway để kết nối nhiều VPC, tìm hiểu mô hình mạng ở quy mô doanh nghiệp và thực hiện dọn dẹp tài nguyên sau khi hoàn thành. |

---

## Kết quả đạt được

* Hoàn thành các hàm AWS Lambda xử lý dữ liệu cho hệ thống giám sát điện năng.
* Kết nối thành công Lambda với Amazon DynamoDB để lưu trữ và truy xuất dữ liệu.
* Hiểu được quy trình triển khai ứng dụng Serverless trên AWS.
* Nắm được sự khác biệt giữa VPC Peering và AWS Transit Gateway trong việc mở rộng hệ thống mạng.
* Biết cách triển khai Hybrid DNS bằng Amazon Route 53 Resolver.

---

## Đánh giá

* Hoàn thành 100% mục tiêu của tuần.
* Đã xây dựng được nền tảng xử lý dữ liệu cho hệ thống Smart Home Energy Waste Monitoring.
* Củng cố kiến thức về kiến trúc mạng AWS và các giải pháp kết nối giữa nhiều VPC.

---

## Kế hoạch tuần tiếp theo

* Khởi tạo Amazon API Gateway và xây dựng các RESTful APIs.
* Tích hợp API Gateway với các hàm AWS Lambda.
* Kiểm thử API bằng Postman và chuẩn bị cho quá trình triển khai hệ thống.