---
title : "Lambda API Handler"
date : 2024-01-01
weight : 13
chapter : false
pre : " <b> 5.13. </b> "
---

#### Tổng quan

Trong phần này, bạn sẽ tạo và cấu hình hàm **Lambda API Handler**. Hàm này chịu trách nhiệm xử lý các yêu cầu từ API Gateway và tương tác với DynamoDB để lấy dữ liệu báo cáo lãng phí năng lượng cũng như các dữ liệu telemetry.

#### Nội dung

- [Tạo Lambda API Handler](5.13.1-create-lambda/)
- [Điều chỉnh Timeout](5.13.2-adjust-timeout/)
- [Cấu hình biến môi trường](5.13.3-config-env-vars/)
- [Cấp quyền đọc DynamoDB](5.13.4-grant-ddb-permissions/)
- [Triển khai mã nguồn](5.13.5-deploy-source-code/)
- [Test Lambda trực tiếp](5.13.6-test-lambda-directly/)
- [Tạo Lambda Integration trong API Gateway](5.13.7-create-lambda-integration/)
- [Gắn Integration vào các Routes](5.13.8-attach-integration-to-routes/)
- [Kiểm tra quyền API Gateway trên Lambda](5.13.9-check-resource-policy/)
- [Kiểm tra API không có JWT](5.13.10-test-api-unauthorized/)