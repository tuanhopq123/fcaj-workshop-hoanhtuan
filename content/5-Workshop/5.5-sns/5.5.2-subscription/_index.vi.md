---
title: "5.5.2 Đăng ký Email Subscription & Xác thực"
weight: 2
description: "Liên kết địa chỉ Email nhận thông báo với SNS Topic và thực hiện bước xác thực Subscription."
---

# 5.5.2 Tạo và Xác nhận Email Subscription

Sau khi Topic được khởi tạo, chúng ta cần liên kết một điểm cuối nhận tin (Endpoint) cụ thể nhằm phân phối cảnh báo[cite: 2]. Trong bài học này, chúng ta dùng giao thức thư điện tử Email[cite: 2].

### Bước 1: Khởi tạo Subscription trên Console

1. Ngay tại trang thông tin chi tiết của topic `energy-waste-alert-topic`, chuyển sang tab **Subscriptions** ở phía dưới[cite: 2].
2. Bấm chọn nút **Create subscription**[cite: 2].
3. Thực hiện điền cấu hình chi tiết như sau[cite: 2]:
   * **Topic ARN:** Giữ nguyên giá trị mặc định liên kết với topic vừa tạo[cite: 2].
   * **Protocol:** Bấm menu xổ xuống và chọn tùy chọn **Email**[cite: 2].
   * **Endpoint:** Nhập chính xác địa chỉ Email cá nhân của bạn (đây sẽ là nơi nhận thư cảnh báo thực tế)[cite: 2].

![Thiết lập thông tin Email Subscription](/images/5-Workshop/5.5-sns/sns-topic-created.png)

4. Nhấn nút **Create subscription** để ghi nhận yêu cầu đăng ký[cite: 2].

---

### Bước 2: Xác thực Subscription từ Hộp thư cá nhân

Hệ thống bảo mật của AWS đòi hỏi chủ sở hữu Endpoint phải xác nhận sự đồng ý nhận tin[cite: 2].

1. Đăng nhập vào hòm thư điện tử cá nhân mà bạn vừa điền ở bước trên[cite: 2].
2. Tìm kiếm thư mới được gửi đến từ **AWS Notifications**[cite: 2].
3. Mở nội dung thư và nhấp vào liên kết đường dẫn **Confirm subscription**[cite: 2].

Giao diện trình duyệt web sẽ mở ra một tab mới hiển thị thông báo **Subscription confirmed!** kèm theo thông tin mã nhận diện ID[cite: 2].

![Trình duyệt hiển thị Subscription confirmed](/images/5-Workshop/5.5-sns/sns-create-email-subscription.png)

---

### Bước 3: Kiểm tra trạng thái trên AWS Console

1. Quay trở lại giao diện **AWS Console** theo đường dẫn `SNS` ➔ `Topics` ➔ `energy-waste-alert-topic`[cite: 2].
2. Kiểm tra danh sách hiển thị ở khu vực **Subscriptions** (Nhấn nút tải lại trang/Refresh nếu giao diện chưa cập nhật)[cite: 2].
3. Xác nhận cột trạng thái chuyển từ *Pending confirmation* sang màu xanh lá cây: **Confirmed**[cite: 2].

![Xác thực trạng thái Confirmed hoàn tất](/images/5-Workshop/5.5-sns/sns-subscription-confirmed.png)