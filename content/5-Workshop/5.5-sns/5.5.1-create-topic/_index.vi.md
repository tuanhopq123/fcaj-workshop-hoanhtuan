---
title: "5.5.1 Khởi tạo SNS Topic"
weight: 1
description: "Cấu hình phân loại Standard Topic kèm định danh Name và Display Name phục vụ phát thông điệp."
---

# 5.5.1 Tạo SNS Topic mới

Tiến hành thiết lập các tham số định danh cốt lõi cho kênh thông báo (Topic) theo quy chuẩn dưới đây[cite: 2]:

### Các thông số cấu hình cụ thể:

* **Type:** Lựa chọn loại hình **Standard**[cite: 2].
* **Name:** `energy-waste-alert-topic`[cite: 2]
* **Display name - optional:** `EnergyWasteAlert`[cite: 2]

> 💡 **Mẹo thiết lập:** Khác với định dạng FIFO yêu cầu quản lý nghiêm ngặt về thứ tự, chế độ **Standard** cung cấp hiệu năng truyền tải thông tin tối đa, hỗ trợ đa dạng giao thức như Lambda, Email, SQS và hoàn toàn đáp ứng tốt bài toán cảnh báo lãng phí năng lượng của workshop[cite: 2].

![Cấu hình thuộc tính SNS Topic](sns-topic-config.png)

Sau khi hoàn tất việc điền các thông tin trên, cuộn chuột xuống cuối trang và nhấn chọn nút **Create topic**[cite: 2].

Hệ thống sẽ chuyển hướng và hiển thị một biểu ngữ thông báo màu xanh lá cây với nội dung: *"Topic energy-waste-alert-topic created successfully."*[cite: 2] để xác nhận tiến trình tạo thành công[cite: 2].

![Xác nhận Topic khởi tạo thành công](sns-topic-created.png)