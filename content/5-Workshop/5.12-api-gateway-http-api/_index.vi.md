---
title : "API Gateway HTTP API"
date : 2024-01-01
weight : 12
chapter : false
pre : " <b> 5.12. </b> "
---

#### Tổng quan

Trong phần này, chúng ta sẽ tạo **HTTP API** bằng Amazon API Gateway. API này sẽ đóng vai trò là cổng tiếp nhận yêu cầu cho backend, xử lý các request từ dashboard và được bảo vệ bởi JWT authorizer.

#### Nội dung

- [Tạo HTTP API](5.12.1-create-http-api/)
- [Tạo các API Routes](5.12.2-create-api-routes/)
- [Chuẩn bị thông tin Amazon Cognito](5.12.3-prepare-cognito-info/)
- [Tạo JWT Authorizer](5.12.4-create-jwt-authorizer/)
- [Gắn JWT Authorizer vào các Routes](5.12.5-attach-authorizer/)
- [Cấu hình CORS](5.12.6-configure-cors/)
- [Kiểm tra Stage $default](5.12.7-check-default-stage/)