---
title : "Cấu hình Rate mỗi 1 phút"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.9.2 </b> "
---

1. **Chọn loại Schedule**
   + Tại **Schedule type**, chọn: **Rate-based schedule**.
   + Không chọn: `Cron-based schedule`[cite: 12].
   + Nhập `rate(1 minute)` vào ô **Rate expression**, hoặc điền **Value:** `1` và **Unit:** `minute`[cite: 12]. Lưu ý dùng số ít `minute`, không nhập `minutes`[cite: 12].

2. **Flexible time window**[cite: 12]
   + Tại **Flexible time window**, chọn: **Off**[cite: 12].
   + Khi bị tắt, Scheduler không được phép trì hoãn invocation[cite: 12].

3. **Timeframe**[cite: 12]
   + Giữ **Start date and time** và **End date and time** để trống[cite: 12].
   + Có thể giữ Timezone là **UTC**[cite: 12].

4. Bấm: **Next**[cite: 12].

![Rate Settings](/images/5-Workshop/5.9-EventBridge/01-cau-hinh-schedule-moi-phut.png)