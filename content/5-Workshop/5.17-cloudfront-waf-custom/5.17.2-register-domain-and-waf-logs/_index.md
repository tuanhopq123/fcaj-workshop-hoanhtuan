---
title : "Tìm kiếm Domain và Kiểm tra WAF Logs"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.17.2. </b> "
---

#### A. Tìm kiếm và Đăng ký Domain

1. Mở **Amazon Route 53**.
2. Chọn: **Domains** -> **Registered domains**.
3. Bấm: **Register domains**.
4. Trong ô tìm kiếm, nhập chính xác: `energywastelab.site` (hoặc tên miền bạn chọn).
5. Bấm: **Search**.

![Tìm kiếm Domain](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-search-domain.png)

6. Chọn `energywastelab.com` (15 USD/năm).
7. Bấm nút: **Proceed to checkout**.

![Chọn Domain](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-select-domain.png)

*Để tránh năm sau AWS tự động thu phí gia hạn:*
8. Giữ nguyên: **Duration: 1 year**.
9. **Bỏ dấu tích** tại: **Auto-renew — On**.
10. Bấm nút: **Next**.

![Cấu hình gia hạn](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-disable-autorenew.png)

11. Nhập **Thông tin liên hệ** và bấm **Next**.

![Thông tin liên hệ](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-contact-info.png)

12. Bấm **Next** để hoàn tất đăng ký.

![Xác nhận đăng ký](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-confirm-registration.png)

*Lưu ý: Nếu đăng ký gặp lỗi, bạn thực hiện bước kiểm tra log dưới đây.*

#### B. Kiểm tra AWS WAF logs

1. Quay lại **AWS Amplify** -> ứng dụng `energy-waste-dashboard`.
2. Chọn: **Hosting** -> **Firewall**.
3. Kiểm tra trạng thái hiển thị: **Web Application Firewall — Enabled**.
4. Bấm nút: **View WAF logs**.

![Xem WAF logs](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-view-waf-logs.png)

5. Trên thanh tab phía trên, bấm: **Associated AWS resources**.
6. Xác nhận Web ACL đang bảo vệ đúng tài nguyên:
   - **Name**: `energy-waste-dashboard`
   - **Resource type**: `Amplify Application`
   - **Associated AWS resources**: `1`

![Tài nguyên liên kết](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-associated-resources.png)