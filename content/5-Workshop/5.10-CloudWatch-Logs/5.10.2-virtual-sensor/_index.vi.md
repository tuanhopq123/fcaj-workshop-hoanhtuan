---
title : "Kiểm tra Virtual Sensor Logs"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.10.2 </b> "
---

1. Bấm vào: `/aws/lambda/energy-virtual-sensor`[cite: 13].
2. Bạn sẽ thấy danh sách Log streams[cite: 13]. Tìm cột: **Last event time**[cite: 13]. Chọn log stream có thời gian mới nhất[cite: 13].
3. Nếu chưa thấy log mong muốn: Tìm bộ chọn thời gian phía trên. Chọn **Relative**, rồi chọn **Last 1 hour** hoặc **Last 3 hours** và bấm Apply[cite: 13].
4. Trong ô tìm kiếm hoặc filter log events, nhập: `eventbridge-scheduler` hoặc `Received trigger event`[cite: 13].
5. Bạn cần tìm đoạn log tương tự[cite: 13]:

```text
Received trigger event: {"source": "eventbridge-scheduler", "forceWaste": false}