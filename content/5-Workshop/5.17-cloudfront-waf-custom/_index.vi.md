---
title : "Cấu hình tùy chỉnh CloudFront WAF"
date : 2024-01-01
weight : 17
chapter : false
pre : " <b> 5.17. </b> "
---

#### Tổng quan

Trong phần này, chúng ta sẽ thực hiện cấu hình **AWS WAF (Web Application Firewall)** để bảo vệ ứng dụng đang được lưu trữ trên AWS Amplify. Bằng cách tích hợp WAF, chúng ta thêm một lớp bảo mật quan trọng, giúp bảo vệ dashboard khỏi các lỗ hổng web phổ biến, bot độc hại và lưu lượng truy cập trái phép. Chúng ta sẽ cùng thực hiện thiết lập tường lửa, cấu hình các quy tắc bảo mật và xác minh log để đảm bảo dashboard luôn trong trạng thái an toàn nhất.

#### Nội dung

- [Thiết lập Amplify WAF](5.17.1-setup-amplify-waf/)
- [Tìm kiếm Domain và Kiểm tra WAF Logs](5.17.2-register-domain-and-waf-logs/)
- [Kiểm tra các rule bảo vệ](5.17.3-check-waf-rules/)
- [Kiểm tra trang Custom domains lần cuối](5.17.4-check-custom-domains/)