---
title : "Tắt tự đăng ký công khai"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.11.5 </b> "
---

Dashboard giám sát phòng lab chỉ nên dành cho người được cấp tài khoản[cite: 14]. Vì vậy, trong giai đoạn workshop, ta tạo người dùng bằng quản trị viên thay vì cho bất kỳ ai tự đăng ký[cite: 14].

1. Trong menu user pool, chọn: **Sign-up**[cite: 14].
2. Tìm phần: **Self-service sign-up**[cite: 14].
3. Bấm: **Edit**[cite: 14].
4. Tắt tùy chọn: **Enable self-registration**[cite: 14].
5. Bấm: **Save changes**[cite: 14].

Khi self-registration bị tắt, người dùng không thể tự đăng ký tài khoản; tài khoản phải được tạo bởi quản trị viên trong Cognito Console hoặc qua API[cite: 14].

![Disable Sign up](/images/5-Workshop/5.11-Cognito/Enable self-registration.png)