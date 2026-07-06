---
title: "5.7.2. Cấu hình Biến Môi Trường"
date: 2026-07-05
weight: 2
---

Việc sử dụng Environment Variables giúp mã nguồn linh hoạt lấy các giá trị cấu hình động (như IoT Topic hay Room ID) mà không cần phải viết cứng (hard-code) trực tiếp trong script.

1. In trong giao diện quản lý Lambda `energy-virtual-sensor`, chuyển sang tab **Configuration**.
2. Chọn mục **Environment variables** ở menu bên trái rồi bấm **Edit**.
3. Tiến hành cấu hình 2 biến môi trường cốt lõi theo hướng dẫn *(Tham chiếu tệp `02-environment-variables-virtual-sensor1.png`)*:
    ![Cấu hình giá trị biến môi trường](/images/5-Workshop/5.7-lambda-virtual-sensor/02-environment-variables-virtual-sensor1.png)
   * **Biến 1**: `Key = IOT_TOPIC` | `Value = home/lab/telemetry`
   * **Biến 2**: `Key = DEFAULT_ROOM_ID` | `Value = lab-01`
4. Bấm **Save** để áp dụng. Hệ thống sẽ cập nhật trạng thái thành công như hiển thị tại tệp `02-environment-variables-virtual-sensor2.png`.
![Danh sách biến môi trường đã lưu](/images/5-Workshop/5.7-lambda-virtual-sensor/02-environment-variables-virtual-sensor2.png)