---
title: "5.18.12. Xóa IAM Roles của Lambda"
date: 2026-07-07
weight: 12
---

Các Lambda Execution Role do AWS Console tự động khởi tạo sẽ không tự biến mất khi hàm Lambda bị xóa, do đó chúng cần được thu hồi riêng lẻ.

#### 12.1. Mở trang quản trị IAM Roles
1. Tìm kiếm từ khóa cụm từ **IAM** và mở bảng điều khiển quản trị phân quyền Identity and Access Management.
2. Trong menu điều hướng bên trái, bấm chọn danh mục **Roles**.

#### 12.2. Tìm kiếm các Role liên quan đến Project
Sử dụng thanh bộ lọc tìm kiếm để quét theo từng từ khóa tên định danh vai trò đặc thù sau:
* `energy-waste-detector`
* `energy-virtual-sensor`
* `energy-api-handler`
* `energy-report-generator`
* `energy-virtual-sensor-every-minute`
* `energy-daily-report`

#### 12.3. Tiến hành gỡ bỏ tuần tự từng thực thể Role
Với mỗi Role tìm được khớp thông tin lọc ở trên, thực hiện chuỗi thao tác:
1. Bấm trực tiếp vào liên kết văn bản hiển thị tên của Role để truy cập giao diện thông tin chi tiết.
2. Kiểm tra mốc thời gian hoạt động cuối cùng tại mục **Last activity** kết hợp chính sách đính kèm để chắc chắn Role này chỉ thuộc phạm vi dự án bài Lab hiện tại.

![Kiểm tra thông tin IAM Role](/images/5-Workshop/5.18-CleanUp/Picture13.png)

3. Quay trở lại giao diện danh mục tổng hợp danh sách **Roles**.
4. Đánh dấu tích chọn vào hộp kiểm đứng trước Role cần giải phóng hạ tầng và chọn **Delete**.
5. Nhập chính xác chuỗi ký tự định danh tên Role đó vào trường văn bản xác thực và chọn **Delete**.

![Xác nhận cấu hình xóa IAM Role](/images/5-Workshop/5.18-CleanUp/Picture14.png)