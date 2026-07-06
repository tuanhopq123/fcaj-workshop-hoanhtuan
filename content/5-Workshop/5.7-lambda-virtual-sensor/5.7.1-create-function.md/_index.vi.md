---
title: "5.7.1. Khởi tạo Hàm Lambda"
date: 2026-07-05
weight: 1
---

1. Tại ô tìm kiếm trên AWS Management Console, nhập `Lambda` và chọn dịch vụ **Lambda**.
2. Trong danh mục điều hướng bên trái, bấm chọn **Functions**.
3. Bấm nút **Create function** *(Minh họa chi tiết xem tại tệp `01-tao-lambda-virtual-sensor1.png`)*.
    ![Giao diện Lambda Functions](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda1.png)
4. Tại trang cấu hình, thực hiện thiết lập các thông tin cơ bản:
   * **Phương thức**: Chọn **Author from scratch**.
   * **Function name**: Nhập `energy-virtual-sensor`.
   * **Runtime**: Chọn **Python 3.14**.
   * **Advanced settings**: Giữ nguyên cấu hình mặc định hoặc tắt các tùy chọn nâng cao.
5. Kiểm tra lại toàn bộ thông tin đã điền *(Minh họa chi tiết xem tại tệp `01-tao-lambda-virtual-sensor2.png`)* và bấm 
   ![Cấu hình thông tin cơ bản Lambda function](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda2.png)
   **Create function**.
6. Sau khi khởi tạo thành công, hệ thống sẽ mở ra giao diện quản lý hàm *(Hiển thị chi tiết tại tệp `01-tao-lambda1.png` và tệp `01-tao-lambda2.png`)*.
  ![Tổng quan hàm Lambda sau khi tạo](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda-virtual-sensor1.png)
   ![Thuộc tính Runtime và mã hash hàm Lambda](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda-virtual-sensor2.png)