---
title: "5.6. Xây dựng Lambda Energy Waste Detector"
date: 2026-07-01T18:00:00+07:00
draft: false
weight: 6
tags: ["aws", "lambda", "dynamodb", "sns"]
categories: ["Workshop"]
description: "Tổng quan về việc xây dựng hàm AWS Lambda để phát hiện lãng phí năng lượng, lưu telemetry vào DynamoDB và gửi cảnh báo qua SNS."
---

AWS Lambda chạy hàm `energy-waste-detector`, xử lý dữ liệu telemetry gửi đến, quyết định xem có đang lãng phí năng lượng hay không, lưu kết quả vào DynamoDB và gửi cảnh báo qua SNS khi cần.

Trong phần này, chúng ta sẽ thực hiện 8 bước chính:

### 1. [Mở AWS Lambda](5.6.1-open-lambda/)
Hướng dẫn cách truy cập console AWS Lambda và bắt đầu tạo function.

### 2. [Tạo function energy-waste-detector](5.6.2-create-function/)
Hướng dẫn từng bước để tạo Lambda function sử dụng runtime Python 3.14.

### 3. [Thêm Environment Variables](5.6.3-add-environment-variables/)
Cách cấu hình các biến môi trường `DDB_TABLE`, `SNS_TOPIC_ARN` và `POWER_THRESHOLD_W`.

### 4. [Cấp quyền IAM cho Lambda](5.6.4-configure-iam-permissions/)
Cách cấp quyền cho function để ghi vào DynamoDB và gửi tin nhắn qua SNS, cũng như cách thêm code cho function.

### 5. [Test Lambda Waste Detector](5.6.5-test-lambda-function/)
Cách tạo và chạy một test event mô phỏng tình huống lãng phí năng lượng.

### 6. [Kiểm tra kết quả Test](5.6.6-check-test-result/)
Cách kiểm tra việc thực thi test đã thành công và trả về kết quả đúng như mong đợi.

### 7. [Kiểm tra DynamoDB](5.6.7-check-dynamodb/)
Cách xác nhận các item telemetry và alert mới đã được lưu vào bảng.

### 8. [Kiểm tra email cảnh báo](5.6.8-check-alert-email/)
Cách kiểm tra email cảnh báo lãng phí năng lượng đã được nhận.
