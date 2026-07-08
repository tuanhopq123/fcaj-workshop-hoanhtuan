---
title : "Define your application"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.11.2 </b> "
---

1. **Application type**
   * Tại Application type, chọn: **Single-page application (SPA)**.
   * Không chọn: *Traditional web application, Machine-to-machine application, Mobile application*.
   * *(Dashboard Next.js/React chạy trong trình duyệt là public client, vì vậy app client không nên chứa client secret)*.

2. **Name your application**
   * Tại Application name, nhập: `energy-waste-dashboard-client`.

3. **Sign-in identifiers**
   * Tại Options for sign-in identifiers, chỉ chọn: **Email**.
   * Bỏ chọn Username hoặc Phone number nếu có. Người dùng sẽ đăng nhập bằng email và mật khẩu.

4. **Required attributes for sign-up**
   * Tại Required attributes for sign-up, chọn: **Email**.

5. **Add a return URL**
   * Tại Return URL, nhập: `http://localhost:3000/`.
   * *(URL này dùng trong giai đoạn phát triển dashboard trên máy tính cục bộ)*.

6. Kiểm tra lại cấu hình rồi bấm: **Create your application**.
7. Sau khi trang Set up your application xuất hiện, kéo xuống dưới và bấm: **Go to overview**.

![Define App](/images/5-Workshop/5.11-Cognito/01-cognito-application-settings.png)