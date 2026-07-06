---
title : "Tạo các API Routes"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.12.2. </b> "
---

Route của HTTP API gồm hai thành phần: HTTP method và resource path (ví dụ: `GET /rooms`). Chúng ta cần tạo chính xác năm route sau:

- `GET /rooms`
- `GET /telemetry`
- `GET /alerts`
- `GET /reports`
- `GET /reports/{date}`

#### Cách thực hiện

1. Trong menu bên trái, chọn: **Develop** -> **Routes**.
2. Trong khung **Routes for energy-waste-http-api**, bấm: **Create**.
3. Lần lượt tạo từng route bằng cách nhập **Method** và **Path** như sau:

| Method | Path |
| :--- | :--- |
| **GET** | `/rooms` |
| **GET** | `/telemetry` |
| **GET** | `/alerts` |
| **GET** | `/reports` |
| **GET** | `/reports/{date}` |

*Lưu ý: Đối với route cuối cùng, bạn phải giữ nguyên dấu ngoặc nhọn: `{date}`.*

4. Sau khi tạo xong, kiểm tra để đảm bảo cả năm route đã xuất hiện trong danh sách bên trái.

![Tạo các API Routes](/images/5-Workshop/5.12-api-gateway/5.12.2-create-routes.png)