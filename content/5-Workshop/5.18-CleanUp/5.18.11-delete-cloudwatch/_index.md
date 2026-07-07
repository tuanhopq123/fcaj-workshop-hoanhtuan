---
title: "5.18.11. Delete CloudWatch Log Groups"
date: 2026-07-07
weight: 11
---

Deleting your Lambda functions does not automatically delete their corresponding Log Groups. You must clean them up separately within CloudWatch Logs.

1. Search for **CloudWatch** and open the application management panel.
2. In the left navigation tree, select **Logs** $\rightarrow$ **Log groups**.
3. Find and check the boxes for the following specific log group streams:
   * `/aws/lambda/energy-waste-detector`
   * `/aws/lambda/energy-virtual-sensor`
   * `/aws/lambda/energy-api-handler`
   * `/aws/lambda/energy-report-generator`
   * `/aws/amplify/d2ppdnlr5ik3e8`
4. Click **Actions** $\rightarrow$ **Delete log group(s)**.

![Select CloudWatch Log Groups](/images/5-Workshop/5.18-CleanUp/Picture11.png)

5. Review the target items and click **Delete** to confirm permanent removal.

![Confirm CloudWatch Deletion](/images/5-Workshop/5.18-CleanUp/Picture12.png)