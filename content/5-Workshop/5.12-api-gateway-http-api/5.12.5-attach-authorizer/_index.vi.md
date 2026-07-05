---
title : "Gắn JWT Authorizer vào các Routes"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.12.5. </b> "
---

JWT Authorizer chỉ bảo vệ những route được gắn authorizer. Request không có token phù hợp sẽ bị API Gateway từ chối trước khi gọi backend.

#### Cách thực hiện

1. Vẫn ở trang: **Develop** -> **Authorization**.
2. Tìm danh sách các routes.
3. Chọn: `GET /rooms`
4. Bấm: **Attach authorizer**.
5. Chọn: `energy-waste-jwt-authorizer`
6. Phần **Authorization scopes** để trống.
7. Bấm: **Attach authorizer** (hoặc **Save**).
8. Thực hiện tương tự cho các route còn lại:
   - `GET /telemetry`
   - `GET /alerts`
   - `GET /reports`
   - `GET /reports/{date}`

![Gắn JWT Authorizer](/images/5-Workshop/5.12-api-gateway/5.12.5-attach-authorizer.png)