---
title : "Cấu hình CORS"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.12.6. </b> "
---

Dashboard chạy tại `http://localhost:3000`, trong khi API Gateway sử dụng domain khác. Do đó, cần CORS để trình duyệt cho phép dashboard gọi API.

#### Thực hiện

1. **Mở CORS**: Trong menu bên trái, chọn **Develop** -> **CORS**. Bấm **Configure** (hoặc **Edit**).
2. **Allow origins**: Nhập `http://localhost:3000` (Lưu ý: Không nhập dấu `/` cuối). Bấm **Add** nếu có nút này.
3. **Allow headers**: Thêm lần lượt `authorization` và `content-type`. Mỗi giá trị nhập xong phải bấm **Add**.
4. **Allow methods**: Chọn **GET** và **OPTIONS**.
5. **Expose headers**: Để trống.
6. **Max age**: Nhập `300`.
7. **Allow credentials**: Giữ **Off** (hoặc bỏ chọn).
8. **Lưu**: Bấm **Save**.

![Cấu hình CORS](/images/5-Workshop/5.12-api-gateway/5.12.6-configure-cors.png)