---
title: "5.6.2 Env variables"
weight: 1
---

# 5.6.2 Cấu hình biến môi trường (Environment Variables)

Thay vì viết cứng (hardcode) các thông số hệ thống như tên bảng hoặc mã ARN của topic, chúng ta sẽ sử dụng các biến môi trường để tối ưu hóa việc quản lý cấu hình cho hàm Lambda.

### Các bước thực hiện:

1. Truy cập vào trang quản trị chi tiết của hàm **energy-waste-detector** vừa tạo.
2. Nhấp chọn tab **Configuration** trên thanh menu chức năng chính.
3. Tại danh mục phụ ở phía bên trái, nhấn chọn mục **Environment variables**.
4. Nhấp chọn nút **Edit** ở góc bên phải.
5. Nhấn **Add environment variable** và điền chính xác 3 cặp giá trị (Key-Value) dưới đây:
   * **Key:** `DDB_TABLE` | **Value:** `EnergyWasteData`
   * **Key:** `SNS_TOPIC_ARN` | **Value:** `arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic`
   * **Key:** `POWER_THRESHOLD_W` | **Value:** `120`
6. Nhấn nút **Save** để lưu lại toàn bộ cấu hình biến môi trường.