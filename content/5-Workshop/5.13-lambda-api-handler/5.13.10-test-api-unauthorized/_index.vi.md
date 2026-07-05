---
title : "Kiểm tra API không có JWT"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b> 5.13.10. </b> "
---

Do cả năm route đã được bảo vệ bằng JWT Authorizer, việc mở route trực tiếp trong trình duyệt mà không gửi token bắt buộc phải bị từ chối.

#### Thực hiện

1. Vào: **API Gateway** -> **Stages** -> `$default`.
2. Sao chép **Invoke URL**.
3. Thêm `/rooms` vào cuối đường dẫn. Ví dụ: `https://<API-ID>.execute-api.ap-southeast-1.amazonaws.com/rooms`
4. Mở URL này trong một tab mới.

#### Kết quả đúng
Bạn sẽ nhận được:
- `401 Unauthorized`
- HOẶC: `{ "message": "Unauthorized" }`

*Lưu ý: Đây là kết quả đúng, chứng minh JWT Authorizer đang chặn request không có token trước khi request đi đến Lambda. Không tháo authorizer chỉ để tránh lỗi 401. Việc kiểm tra API với JWT hợp lệ sẽ được thực hiện khi dashboard Next.js đăng nhập Cognito và gửi header `Authorization: Bearer <JWT>`.*

![Kiểm tra API không có JWT](/images/5-Workshop/5.13-lambda-api-handler/5.13.10-test-unauthorized.png)