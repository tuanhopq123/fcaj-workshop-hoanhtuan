---
title : "Disable Schedule"
date : 2026-07-05
weight : 5
chapter : false
pre : " <b> 5.9.5 </b> "
---

This step is mandatory to prevent the system from continuously creating telemetry, logs, and emails.

1. Go back to: **Amazon EventBridge → Scheduler → Schedules**.
2. Choose the schedule: `schedule_virtual_sensor_every_1_min`.
3. Click: **Disable** (or go to Edit -> Disable schedule -> Save).
4. Verify the status is now **Disabled**.

![Disable](/images/5-Workshop/5.9-EventBridge/05-disable-schedule.png)