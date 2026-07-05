---
title : "Tạo JWT Authorizer"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.12.4. </b> "
---

#### A. Mở Authorization

1. Quay lại tab API Gateway.
2. Bảo đảm bạn đang ở đúng API: `energy-waste-http-api`.
3. Trong menu bên trái, chọn: **Develop** -> **Authorization**.
4. Tìm phần: **Manage authorizers**.
5. Bấm: **Create** (hoặc **Create authorizer**).

#### B. Nhập thông tin Authorizer

1. **Authorizer name**: `energy-waste-jwt-authorizer`
2. **Authorizer type**: Chọn **JWT** (Không chọn Lambda).
3. **Identity source**: Nhập chính xác: `$request.header.Authorization`
   - *Kiểm tra:* Có ký tự `$` ở đầu, dấu chấm giữa `request`, `header` và `Authorization`, viết hoa chữ `A` trong `Authorization`.
4. **Issuer URL**: Dán Issuer URL đã chuẩn bị theo dạng:
   `https://cognito-idp.ap-southeast-1.amazonaws.com/<USER_POOL_ID>`
   *(Ví dụ: `https://cognito-idp.ap-southeast-1.amazonaws.com/ap-southeast-1_AbCdEf123`)*
5. **Audience**: Dán **App Client ID** của `energy-waste-dashboard-client`.
   - *Quan trọng:* Nếu giao diện có nút **Add**, hãy bấm **Add** sau khi dán. Giá trị phải xuất hiện trong danh sách; chỉ nhập vào ô mà chưa bấm Add thì giá trị chưa được lưu.
6. **Authorization scopes**: Để trống.

![Cấu hình Authorizer](/images/5-Workshop/5.12-api-gateway/5.12.4-configure-authorizer.png)

7. Bấm: **Create**.

Sau khi bấm Create:

![Authorizer đã tạo](/images/5-Workshop/5.12-api-gateway/5.12.4-authorizer-created.png)