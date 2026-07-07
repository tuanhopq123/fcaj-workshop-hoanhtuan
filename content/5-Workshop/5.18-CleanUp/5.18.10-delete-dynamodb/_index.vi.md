---
title: "5.18.10. Xóa bảng Amazon DynamoDB"
date: 2026-07-07
weight: 10
---

Xóa bảng DynamoDB sẽ xóa vĩnh viễn toàn bộ các thực thể dữ liệu dự án bao gồm Rooms, Telemetry, Alerts và Reports Metadata. Đây là tác vụ hệ thống không thể hoàn tác phục hồi.

1. Tìm kiếm cụm từ **DynamoDB** và truy cập vào trang quản trị dịch vụ.
2. Trong menu bên trái, bấm chọn danh mục **Tables**.
3. Đánh dấu tích chọn vào bảng dữ liệu: `EnergyWasteData`.
4. Chọn nút hành động **Delete**.

![Chọn bảng DynamoDB](/images/5-Workshop/5.18-CleanUp/Picture9.png)

5. Nhập từ khóa xác nhận `confirm` và chọn **Delete table** để hoàn tất dọn dẹp cơ sở dữ liệu.

![Bảng DynamoDB đã xóa thành công](/images/5-Workshop/5.18-CleanUp/Picture10.png)****