---
title : "Kiểm tra Stage $default"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.12.7. </b> "
---

Stage là điểm triển khai để ứng dụng gọi API. Khi stage `$default` bật **Auto-deploy**, các thay đổi API được triển khai tự động mà không cần bấm nút Deploy thủ công.

#### Thực hiện

1. Trong menu bên trái, chọn: **Deploy** -> **Stages**.
2. Chọn stage: `$default`
3. Kiểm tra: **Auto-deploy: Enabled**
4. Tìm và sao chép: **Invoke URL**.
   - URL có dạng: `https://<API-ID>.execute-api.ap-southeast-1.amazonaws.com`
   - *Lưu ý: Vì sử dụng `$default`, URL gọi route sau này sẽ là: `https://<API-ID>.execute-api.ap-southeast-1.amazonaws.com/rooms`.*

*Lưu ý: Không cần bấm nút Deploy màu cam. Các thay đổi sẽ được triển khai tự động.*

![Kiểm tra Stage $default](/images/5-Workshop/5.12-api-gateway/5.12.7-check-stage.png)