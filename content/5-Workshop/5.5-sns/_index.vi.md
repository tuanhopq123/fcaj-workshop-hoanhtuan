---
title: "5.5. Thiết lập cảnh báo Amazon SNS"
date: 2026-07-01T17:30:00+07:00
draft: false
weight: 5
tags: ["aws", "sns", "notifications"]
categories: ["Workshop"]
description: "Tổng quan về việc thiết lập Amazon SNS để gửi email cảnh báo khi phát hiện lãng phí năng lượng."
---

Amazon SNS (Simple Notification Service) được dùng để gửi email cảnh báo mỗi khi hệ thống phát hiện lãng phí năng lượng, ví dụ như thiết bị vẫn bật trong phòng không có người.

Trong phần này, chúng ta sẽ thực hiện 7 bước chính:

### 1. [Mở Amazon SNS](5.5.1-open-sns/)
Hướng dẫn cách truy cập console Amazon SNS và bắt đầu tạo topic.

### 2. [Tạo SNS Topic](5.5.2-create-topic/)
Hướng dẫn từng bước để tạo topic `energy-waste-alert-topic`.

### 3. [Tạo Email Subscription](5.5.3-create-email-subscription/)
Cách đăng ký một địa chỉ email vào topic để nhận cảnh báo.

### 4. [Xác nhận email SNS](5.5.4-confirm-subscription-email/)
Cách tìm và xác nhận email subscription do AWS gửi.

### 5. [Kiểm tra Subscription status](5.5.5-check-subscription-status/)
Cách kiểm tra trạng thái subscription là **Confirmed**.

### 6. [Test gửi email cảnh báo](5.5.6-test-publish-message/)
Cách gửi một tin nhắn test đến topic để mô phỏng cảnh báo lãng phí năng lượng.

### 7. [Kiểm tra email nhận được](5.5.7-check-received-email/)
Cách kiểm tra email cảnh báo test đã được nhận thành công.
