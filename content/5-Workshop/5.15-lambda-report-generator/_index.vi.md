---
title : "Lambda Report Generator"
date : 2024-01-01
weight : 15
chapter : false
pre : " <b> 5.15. </b> "
---

#### Tổng quan

Trong phần này, bạn sẽ tạo và cấu hình **Lambda Report Generator**. Hàm này có nhiệm vụ truy xuất dữ liệu từ DynamoDB, tổng hợp thông tin và tạo các báo cáo tiêu thụ năng lượng hàng ngày để lưu trữ lên S3.

#### Nội dung

- [Tạo Lambda Report Generator](5.15.1-create-lambda/)
- [Cấu hình Timeout và Memory](5.15.2-config-timeout-memory/)
- [Cấu hình biến môi trường](5.15.3-config-env-vars/)
- [Cấp quyền IAM](5.15.4-grant-iam-permissions/)
- [Triển khai mã nguồn](5.15.5-deploy-source-code/)
- [Tạo Test Event](5.15.6-create-test-event/)
- [Kiểm tra file trên S3](5.15.7-check-s3-file/)
- [Kiểm tra metadata trên DynamoDB](5.15.8-check-ddb-metadata/)
- [Tạo lịch chạy hàng ngày](5.15.9-create-daily-schedule/)
- [Vô hiệu hóa lịch chạy](5.15.10-disable-schedule/)