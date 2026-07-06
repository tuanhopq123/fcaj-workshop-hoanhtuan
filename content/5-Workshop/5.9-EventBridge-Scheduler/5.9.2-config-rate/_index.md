---
title : "Configure Rate"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.9.2 </b> "
---

1. **Choose Schedule type**
   + In **Schedule type**, choose: **Rate-based schedule**.
   + Do not choose: `Cron-based schedule`.
   + Enter `rate(1 minute)` in the **Rate expression** box, or set **Value:** `1` and **Unit:** `minute`. Make sure to use the singular `minute`, not `minutes`.

2. **Flexible time window**
   + In **Flexible time window**, choose: **Off**.
   + When turned off, the Scheduler is not allowed to delay invocation within a flexible time window.

3. **Timeframe**
   + Leave **Start date and time** and **End date and time** blank.
   + Keep Timezone as **UTC** (or local timezone).

4. Click: **Next**.

![Rate Settings](/images/5-Workshop/5.9-EventBridge/01-cau-hinh-schedule-moi-phut.png)