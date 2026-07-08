---
title : "Disable Schedule sau khi test"
date : 2026-07-05 
weight : 5
chapter : false
pre : " <b> 5.9.5 </b> "
---

Đây là bước bắt buộc để tránh hệ thống tiếp tục tạo telemetry, log và email gây lãng phí tài nguyên.

1. Quay lại: **Amazon EventBridge → Scheduler → Schedules**.
2. Chọn schedule: `schedule_virtual_sensor_every_1_min`.
3. Bấm: **Disable** (hoặc chọn Edit -> Disable schedule -> Save).
4. Kiểm tra trạng thái đã chuyển thành: **Disabled**.

![Disable](/images/5-Workshop/5.9-EventBridge/05-disable-schedule.png)