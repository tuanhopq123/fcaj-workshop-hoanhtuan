---
title : "Delete EventBridge Scheduler"
date : 2026-07-05 
weight : 1
chapter : false
pre : " <b> 5.18.1 </b> "
---

You must delete the schedules first so that the Virtual Sensor and Report Generator Lambda functions are not invoked during cleanup.

1. **Open EventBridge Scheduler**
   * Search for `EventBridge` and open Amazon EventBridge.
   * In the left menu, open **Scheduler** -> **Schedules**.

2. **Delete virtual sensor schedule**
   * Find and select `schedule_virtual_sensor_every_1_min`.
   * Click **Delete** and confirm.

3. **Delete report generator schedule**
   * Find and select `schedule_report_daily_0005`.
   * Click **Delete**.

![Delete Schedule 1](/images/5-Workshop/5.18-CleanUp/Xoa-EventBridge-Scheduler.png)
![Delete Schedule 2](/images/5-Workshop/5.18-CleanUp/Xoa-EventBridge-Scheduler2.png)