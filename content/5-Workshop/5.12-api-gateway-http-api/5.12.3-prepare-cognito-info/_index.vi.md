---
title : "Chuẩn bị thông tin Amazon Cognito"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.12.3. </b> "
---

JWT Authorizer cần hai giá trị: **User Pool ID** và **App Client ID**.

#### A. Lấy User Pool ID

1. Mở một tab AWS Console mới.
2. Vào: **Amazon Cognito** -> **User pools** -> `energy-waste-user-pool` -> **Overview**.
3. Tìm mục: **User pool ID**.
4. Bấm biểu tượng sao chép. Giá trị có dạng: `ap-southeast-1_OiGmVapoL`
5. Dán tạm vào Notepad.

![Lấy User Pool ID](/images/5-Workshop/5.12-api-gateway/5.12.3-user-pool-id.png)

#### B. Lấy App Client ID

1. Trong user pool, chọn: **Applications** -> **App clients**.
2. Chọn: `energy-waste-dashboard-client`
3. Tìm mục: **Client ID** (ví dụ: `42bod21u3a1g499u643mt056fm`).
4. Sao chép Client ID và dán vào Notepad.

*Lưu ý: Không sao chép **Client secret**. App client của bạn phải hiển thị: `Client secret: -`*

![Lấy App Client ID](/images/5-Workshop/5.12-api-gateway/5.12.3-client-id.png)