---
title : "Open CloudWatch Logs"
date : 2026-07-05
weight : 1
chapter : false
pre : " <b> 5.10.1 </b> "
---

1. Check the Region in the top right corner: **Asia Pacific (Singapore) ap-southeast-1**.
2. In the AWS Console search bar, type: `CloudWatch`.
3. Choose: **Amazon CloudWatch**.
4. In the left menu, find: **Logs**.
5. Choose either **Log groups** or **Log Management** (depending on the interface).
6. In the log group search box, enter: `energy-`.
7. You should see at least two log groups:
   * `/aws/lambda/energy-virtual-sensor`.
   * `/aws/lambda/energy-waste-detector`.

![CloudWatch Logs](/images/5-Workshop/5.10-CloudWatch/01-cloudwatch-log-groups.png)