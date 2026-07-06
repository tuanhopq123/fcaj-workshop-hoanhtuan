---
title : "Check Virtual Sensor Logs"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.10.2 </b> "
---

1. Click on: `/aws/lambda/energy-virtual-sensor`[cite: 13].
2. You will see a list of Log streams[cite: 13]. Find the column: **Last event time**[cite: 13]. Select the log stream with the newest time[cite: 13].
3. If you haven't seen the expected log, find the time selector at the top. Choose **Relative**, then **Last 1 hour** or **Last 3 hours**, and click Apply[cite: 13].
4. In the search or filter log events box, enter: `eventbridge-scheduler` or `Received trigger event`[cite: 13].
5. You need to find a log snippet similar to[cite: 13]:

```text
Received trigger event: {"source": "eventbridge-scheduler", "forceWaste": false}