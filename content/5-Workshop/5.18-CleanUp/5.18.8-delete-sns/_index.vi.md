---
title: "5.18.8. Xóa Amazon SNS Topic"
date: 2026-07-07
weight: 8
---

Khi xóa SNS Topic, các subscription thuộc Topic đó cũng tự động bị xóa theo, vì vậy bạn không cần phải thực hiện gỡ bỏ email subscription riêng lẻ từ trước.

1. Tìm kiếm cụm từ **SNS** và mở dịch vụ **Amazon Simple Notification Service**.
2. Trong menu điều hướng bên trái, chọn **Topics**.
3. Chọn chính xác kênh thông báo: `energy-waste-alert-topic`.
4. Chọn nút **Delete**.

![Chọn SNS Topic](/images/5-Workshop/5.18-CleanUp/Picture3.png)

5. Nhập chuỗi văn bản xác nhận `delete me` và chọn **Delete** để kết thúc dọn dẹp.

![Xóa SNS Topic thành công](/images/5-Workshop/5.18-CleanUp/Picture4.png)