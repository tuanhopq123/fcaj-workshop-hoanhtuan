---
title : "Delete AWS IoT Rule"
date : 2026-07-05 
weight : 6
chapter : false
pre : " <b> 5.18.6 </b> "
---

You must delete the IoT Rule before deleting the Lambda Waste Detector to avoid having a rule pointing to a non-existent Lambda function.

1. **Open AWS IoT Core**
   * Search for and open **IoT Core**.
   * In the left menu, select **Message routing** -> **Rules**.

2. **Delete Rule**
   * Select `iot_rule_energy_telemetry_to_waste_detector`.
   * Click **Delete**, enter the confirmation string, and verify it is removed.

![Delete Rule 1](/images/5-Workshop/5.18-CleanUp/Xoa-Rule.png)
![Delete Rule 2](/images/5-Workshop/5.18-CleanUp/Xoa-Rule2.png)