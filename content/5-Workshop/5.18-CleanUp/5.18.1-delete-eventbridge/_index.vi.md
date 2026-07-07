---
title : "Xóa EventBridge Scheduler"
date : 2026-07-05 
weight : 1
chapter : false
pre : " <b> 5.18.1 </b> "
---

Phải xóa lịch chạy trước để Lambda Virtual Sensor và Lambda Report Generator không tiếp tục được gọi trong lúc dọn dẹp.

1. **Mở EventBridge Scheduler**
   * Tại thanh tìm kiếm, nhập `EventBridge` và chọn Amazon EventBridge.
   * Trong menu bên trái, mở **Scheduler** -> **Schedules**.

2. **Xóa lịch cảm biến ảo**
   * Tìm và đánh dấu `schedule_virtual_sensor_every_1_min`.
   * Chọn **Delete** và nhập chuỗi xác nhận.

3. **Xóa lịch tạo báo cáo**
   * Tìm và đánh dấu `schedule_report_daily_0005`.
   * Chọn **Delete**.

![Xóa Schedule 1](/images/5-Workshop/5.18-CleanUp/Xoa-EventBridge-Scheduler.png)
![Xóa Schedule 2](/images/5-Workshop/5.18-CleanUp/Xoa-EventBridge-Scheduler2.png)