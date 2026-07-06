---
title : "Tạo Lambda Integration trong API Gateway"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.13.7. </b> "
---

Bây giờ chúng ta sẽ thực hiện kết nối: **API Gateway** -> `energy-api-handler`.

#### Bước 1: Mở Integrations

1. Vào: **API Gateway** -> **APIs** -> `energy-waste-http-api`
2. Trong menu bên trái chọn: **Develop** -> **Integrations**
3. Tìm phần: **Manage integrations**
4. Bấm: **Create** (hoặc **Create and attach an integration**).

#### Bước 2: Chọn Lambda

1. Tại **Integration type**, chọn: **Lambda function**
2. Tại **AWS Region**, chọn: `ap-southeast-1`
3. Tại **Lambda function**, chọn: `energy-api-handler`
4. Tại **Payload format version**, chọn: `2.0`
5. Nếu có **Integration name**, nhập: `energy-api-handler-integration`
6. Giữ nguyên timeout mặc định.
7. Bấm: **Create** (hoặc **Create integration**).

![Tạo Lambda Integration](/images/5-Workshop/5.13-lambda-api-handler/5.13.7-create-integration.png)