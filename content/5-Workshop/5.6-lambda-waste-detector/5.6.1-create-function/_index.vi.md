---
title: "5.6.1 Create function"
weight: 1
---

# 5.6.1 Khởi tạo hàm AWS Lambda

Để bắt đầu xử lý luồng dữ liệu telemetry từ hệ thống IoT, chúng ta cần khởi tạo một hàm tính toán serverless bằng dịch vụ AWS Lambda.

### Các bước thực hiện:

1. Tại thanh tìm kiếm phía trên cùng của **AWS Management Console**, gõ từ khóa `Lambda`.
2. Chọn dịch vụ **Lambda** từ danh sách kết quả tìm kiếm.
3. Ở danh mục menu bên trái, nhấn chọn vào mục **Functions**.
4. Nhấp chọn nút **Create function** ở góc trên bên phải.
5. Tại màn hình **Create function**, thiết lập các thông số cấu hình sau:
   * Chọn tùy chọn **Author from scratch**.
   * **Function name:** `energy-waste-detector`
   * **Runtime:** Chọn phiên bản `Python 3.14`.
6. Cuối cùng, nhấn nút **Create function** ở góc dưới để hoàn tất khởi tạo hàm.