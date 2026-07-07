---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---


## Mục tiêu Tuần 5

* Xây dựng tầng API giao tiếp giữa người dùng và hệ thống bằng Amazon API Gateway.
* Thiết lập Amazon S3 để lưu trữ các tài nguyên tĩnh của hệ thống.
* Hoàn thành các bài thực hành về AWS Backup, Amazon SNS và Amazon S3.
* Tham gia sự kiện FCAJ Community Day để cập nhật kiến thức về AI và Cloud Computing.

---

## Công việc thực hiện trong tuần

| Nội dung | Kết quả |
|----------|----------|
| Amazon API Gateway | Khởi tạo API Gateway và xây dựng các RESTful API phục vụ truy xuất thông tin phòng, dữ liệu cảm biến, cảnh báo và báo cáo của hệ thống giám sát điện năng. Các API được tích hợp trực tiếp với AWS Lambda để xử lý nghiệp vụ. |
| Amazon S3 | Tạo S3 Bucket để lưu trữ các tài nguyên tĩnh như hình ảnh giao diện, tài liệu hệ thống và các tệp phục vụ Dashboard. Đồng thời cấu hình các chính sách bảo mật cơ bản cho Bucket. |
| Lab 13 - AWS Backup & Amazon SNS | Thực hành xây dựng kế hoạch sao lưu tự động cho tài nguyên AWS và tích hợp Amazon SNS để gửi thông báo trạng thái sao lưu qua email. |
| Lab 57 - Amazon S3 | Tìm hiểu cơ chế lưu trữ đối tượng trên Amazon S3, các lớp lưu trữ (Storage Classes), phân quyền truy cập và tối ưu chi phí lưu trữ dữ liệu. |
| Tham gia FCAJ Community Day | Tham dự sự kiện công nghệ về AI và AWS Cloud, tìm hiểu về Context trong AI, Amazon CloudFront, Amazon Q, kiến trúc Multi-Agent và các xu hướng AI hiện đại. |

---

## Kết quả đạt được

* Hoàn thành việc xây dựng tầng API cho hệ thống thông qua Amazon API Gateway.
* Thiết lập thành công Amazon S3 để phục vụ lưu trữ tài nguyên tĩnh.
* Hiểu được quy trình tích hợp API Gateway với AWS Lambda trong kiến trúc Serverless.
* Nắm được cơ chế sao lưu tài nguyên bằng AWS Backup và hệ thống thông báo với Amazon SNS.
* Mở rộng kiến thức về tối ưu hiệu năng và chi phí khi sử dụng Amazon S3 kết hợp Amazon CloudFront.
* Tiếp cận nhiều xu hướng mới về AI, Generative AI và kiến trúc Multi-Agent thông qua FCAJ Community Day.

---

## Đánh giá

* Hoàn thành 100% mục tiêu của tuần.
* Kiến trúc của hệ thống Smart Home Energy Waste Monitoring đã hoàn thiện thêm tầng giao tiếp giữa người dùng và Backend.
* Kiến thức thu được từ các bài Lab và sự kiện giúp hiểu rõ hơn cách xây dựng các ứng dụng AI và Cloud theo tiêu chuẩn thực tế.

---

## Kế hoạch tuần tiếp theo

* Tích hợp Amazon CloudWatch để giám sát toàn bộ hệ thống.
* Thiết lập Logging, Monitoring và CloudWatch Alarms cho các API.
* Tiếp tục thực hiện các bài thực hành AWS theo lộ trình đào tạo.