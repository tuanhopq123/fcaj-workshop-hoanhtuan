---
title : "Gắn Integration vào năm route"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.13.8. </b> "
---

Bây giờ chúng ta sẽ thực hiện gắn integration đã tạo vào năm route đã định nghĩa.

#### Cách thực hiện

1. Trong menu trái, chọn: **Routes**.
2. Chọn route: `GET /rooms`
3. Trong phần **Integration**, bấm: **Attach integration**.
4. Chọn: `energy-api-handler-integration`
5. Bấm: **Attach integration**.
6. Làm tương tự cho bốn route còn lại:
   - `GET /telemetry`
   - `GET /alerts`
   - `GET /reports`
   - `GET /reports/{date}`

#### Kết quả đúng

Cả năm route phải có:
- **Authorization**: `energy-waste-jwt-authorizer`
- **Integration**: `energy-api-handler`

| Route | Authorizer | Integration |
| :--- | :--- | :--- |
| `GET /rooms` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /telemetry` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /alerts` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /reports` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /reports/{date}` | `energy-waste-jwt-authorizer` | `energy-api-handler` |

*Lưu ý: Do `$default` stage đang bật tính năng **Auto-deploy**, nên bạn không cần phải bấm nút Deploy thủ công.*

![Gắn Integration vào route](/images/5-Workshop/5.13-lambda-api-handler/5.13.8-attach-integration.png)