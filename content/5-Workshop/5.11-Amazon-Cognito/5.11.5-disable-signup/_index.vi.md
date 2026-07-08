---
title : "Tắt tự đăng ký công khai"
date : 2026-07-05
weight : 5
chapter : false
pre : " <b> 5.11.5 </b> "
---

Dashboard giám sát phòng lab chỉ nên dành cho người được cấp tài khoản. Vì vậy, trong giai đoạn workshop, ta tạo người dùng bằng quản trị viên thay vì cho bất kỳ ai tự đăng ký.

1. Trong menu user pool, chọn: **Sign-up**.
2. Tìm phần: **Self-service sign-up**.
3. Bấm: **Edit**.
4. Tắt tùy chọn: **Enable self-registration**.
5. Bấm: **Save changes**.

Khi self-registration bị tắt, người dùng không thể tự đăng ký tài khoản; tài khoản phải được tạo bởi quản trị viên trong Cognito Console hoặc qua API.

![Disable Sign up](/images/5-Workshop/5.11-Cognito/Enable self-registration.png)