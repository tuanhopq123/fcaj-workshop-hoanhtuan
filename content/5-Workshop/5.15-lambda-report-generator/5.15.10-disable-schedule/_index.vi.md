---
title : "Disable Schedule sau khi kiểm tra"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b> 5.15.10. </b> "
---

Do Lambda đã được kiểm tra thủ công nên không cần giữ schedule chạy để chờ đến 00:05.

#### Bước 1: Mở Schedule

1. Mở dịch vụ **Amazon EventBridge** -> **Scheduler** -> **Schedules**.
2. Chọn schedule: `schedule_report_daily_0005`

#### Bước 2: Disable Schedule

1. Bấm nút **Disable**.
2. Xác nhận nếu hệ thống AWS yêu cầu.

**Kết quả đúng:**
- **Schedule name**: `schedule_report_daily_0005`
- **Status**: `Disabled`

*Lưu ý: Khi nào cần hệ thống tạo báo cáo tự động mỗi ngày, bạn mới bật (Enable) schedule này trở lại. Schedule chạy cảm biến mỗi phút cũng phải được giữ ở trạng thái tắt (`schedule_virtual_sensor_every_1_min`: Disabled).*

![Disable Schedule sau khi kiểm tra](/images/5-Workshop/5.15-lambda-report/5.15.10-disable-schedule.png)