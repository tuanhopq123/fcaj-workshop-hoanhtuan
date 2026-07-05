---
title : "Tạo Schedule chạy hằng ngày lúc 00:05"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b> 5.15.9. </b> "
---

EventBridge Scheduler sẽ gọi Lambda mỗi ngày lúc `00:05` theo múi giờ `Asia/Ho_Chi_Minh`. Lambda không nhận trường `reportDate` từ Scheduler nên sẽ tự động tạo báo cáo cho ngày hôm trước.

#### Bước 1: Mở EventBridge Scheduler

1. Mở dịch vụ **Amazon EventBridge**.
2. Trong menu bên trái, chọn **Scheduler** -> **Schedules**.
3. Bấm **Create schedule**.

![Mở EventBridge Scheduler](/images/5-Workshop/5.15-lambda-report/5.15.9-step1.png)

#### Bước 2: Nhập Schedule details

1. Tại **Schedule name**, nhập: `schedule_report_daily_0005`
2. Tại **Schedule group**, giữ: `default`
3. Chọn **Recurring schedule**.
4. Chọn **Cron-based schedule**.
5. Tại **Cron expression**, nhập: `cron(5 0 * * ? *)`
6. Tại **Timezone**, chọn: `Asia/Ho_Chi_Minh`
7. Tại **Flexible time window**, chọn: `Off`
8. Bấm **Next**.

![Nhập Schedule details](/images/5-Workshop/5.15-lambda-report/5.15.9-step2.png)

#### Bước 3: Chọn Target

1. Tại phần Target, chọn **Templated target**.
2. Chọn **AWS Lambda Invoke**.
3. Tại **Lambda function**, chọn: `energy-report-generator`
4. Tại **Payload**, dán đoạn JSON sau:

{
  "source": "eventbridge-scheduler"
}

*Lưu ý: Không truyền `reportDate`. Lambda sẽ tự lấy ngày hôm trước theo UTC+7.*

5. Bấm **Next**.

![Chọn Target](/images/5-Workshop/5.15-lambda-report/5.15.9-step3.png)

#### Bước 4: Cấu hình Settings

1. Tại **Schedule state**, chọn: `Enable`
2. Tại **Action after schedule completion**, chọn: `None`
3. Tại **Retry policy**, chọn: `Off`
4. Tại **Dead-letter queue**, chọn: `None`
5. Tại **Encryption**, giữ nguyên: `AWS owned key`
6. Tại phần Permissions, chọn **Create new role for this schedule**.
7. Tại **Role name**, nhập: `eventbridge-scheduler-energy-report-generator-role`
   *(AWS sẽ tự tạo role có quyền `lambda:InvokeFunction` đối với Lambda `energy-report-generator`).*

![Cấu hình Settings](/images/5-Workshop/5.15-lambda-report/5.15.9-step4.png)

#### Bước 5: Kiểm tra và tạo Schedule

Kiểm tra lại toàn bộ thông tin:
- **Name**: `schedule_report_daily_0005`
- **Cron**: `cron(5 0 * * ? *)`
- **Timezone**: `Asia/Ho_Chi_Minh`
- **Target**: `energy-report-generator`
- **Payload**: `{"source": "eventbridge-scheduler"}`
- **Flexible time window**: `Off`
- **Schedule state**: `Enable`

Bấm nút **Create schedule** và chờ thông báo tạo thành công.

![Kiểm tra và tạo Schedule](/images/5-Workshop/5.15-lambda-report/5.15.9-step5.png)