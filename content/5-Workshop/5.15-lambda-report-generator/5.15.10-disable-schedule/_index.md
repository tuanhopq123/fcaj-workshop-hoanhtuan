---
title : "Disable Schedule After Testing"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b> 5.15.10. </b> "
---

Since the Lambda function has already been tested manually, there is no need to leave the schedule running to wait until 00:05.

#### Step 1: Open Schedule

1. Navigate to **Amazon EventBridge** -> **Scheduler** -> **Schedules**.
2. Select the schedule: `schedule_report_daily_0005`

#### Step 2: Disable Schedule

1. Click **Disable**.
2. Confirm the action if AWS prompts you.

**Expected Results:**
- **Schedule name**: `schedule_report_daily_0005`
- **Status**: `Disabled`

*Note: Only enable the schedule again when you need the system to generate reports automatically every day. Ensure the one-minute virtual sensor schedule also remains disabled (`schedule_virtual_sensor_every_1_min`: Disabled).*

![Disable Schedule](/images/5-Workshop/5.15-lambda-report/5.15.10-disable-schedule.png)