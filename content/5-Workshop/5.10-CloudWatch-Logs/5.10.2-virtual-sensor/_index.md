---
title : "Check Virtual Sensor Logs"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.10.2 </b> "
---

1. Click on: `/aws/lambda/energy-virtual-sensor`.
2. You will see a list of Log streams. Find the column: **Last event time**. Select the log stream with the newest time.
3. If you haven't seen the expected log, find the time selector at the top. Choose **Relative**, then **Last 1 hour** or **Last 3 hours**, and click Apply.
4. In the search or filter log events box, enter: `eventbridge-scheduler` or `Received trigger event`.
5. You need to find a log snippet similar to:

```text
Received trigger event: {"source": "eventbridge-scheduler", "forceWaste": false}