---
title: "5.5 Khởi tạo Dịch vụ Thông báo Amazon SNS"
weight: 5
value: 55
description: "Hướng dẫn từng bước truy cập dịch vụ Amazon Simple Notification Service và chuẩn bị tích hợp kênh cảnh báo."
---

Trong phần này, chúng ta sẽ làm việc với **Amazon Simple Notification Service (SNS)**. Dịch vụ nhắn tin được quản lý này cho phép hệ thống của chúng ta đẩy các cảnh báo tiêu thụ điện năng tức thời đến người dùng.

Trong phần này, chúng ta sẽ thực hiện ba bước chính:

### 1. [Tạo SNS Topic](5.5.1-create-topic/)
Các bước chi tiết để truy cập giao diện điều khiển Amazon SNS, bắt đầu quy trình khởi tạo và cấu hình một Topic mới để phát các thông báo.

### 2. [Tạo Subscriptions](5.5.2-subscription/)
Hướng dẫn cách đăng ký các đầu cuối nhận tin của người dùng (như Email hoặc SMS) để đăng ký theo dõi (subscribe) vào Topic vừa tạo nhằm nhận các cảnh báo.

### 3. [Kiểm tra Phát Tin nhắn](5.5.3-test-publish/)
Hướng dẫn cách gửi thử một tin nhắn trực tiếp từ AWS Console để xác minh hệ thống gửi nhận thông báo hoạt động thành công.