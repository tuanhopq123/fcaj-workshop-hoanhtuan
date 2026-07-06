---
title : "Define your application"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.11.2 </b> "
---

1. **Application type**[cite: 14]
   * Tại Application type, chọn: **Single-page application (SPA)**[cite: 14].
   * Không chọn: *Traditional web application, Machine-to-machine application, Mobile application*[cite: 14].
   * *(Dashboard Next.js/React chạy trong trình duyệt là public client, vì vậy app client không nên chứa client secret)*[cite: 14].

2. **Name your application**[cite: 14]
   * Tại Application name, nhập: `energy-waste-dashboard-client`[cite: 14].

3. **Sign-in identifiers**[cite: 14]
   * Tại Options for sign-in identifiers, chỉ chọn: **Email**[cite: 14].
   * Bỏ chọn Username hoặc Phone number nếu có[cite: 14]. Người dùng sẽ đăng nhập bằng email và mật khẩu[cite: 14].

4. **Required attributes for sign-up**[cite: 14]
   * Tại Required attributes for sign-up, chọn: **Email**[cite: 14].

5. **Add a return URL**[cite: 14]
   * Tại Return URL, nhập: `http://localhost:3000/`[cite: 14].
   * *(URL này dùng trong giai đoạn phát triển dashboard trên máy tính cục bộ)*[cite: 14].

6. Kiểm tra lại cấu hình rồi bấm: **Create your application**[cite: 14].
7. Sau khi trang Set up your application xuất hiện, kéo xuống dưới và bấm: **Go to overview**[cite: 14].

![Define App](/images/5-Workshop/5.11-Cognito/01-cognito-application-settings.png)