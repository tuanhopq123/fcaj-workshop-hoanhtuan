---
title : "Create IoT Rule"
date : 2026-07-05 
weight : 2
chapter : false
pre : " <b> 5.8.2 </b> "
---

1. For **Rule name**, enter exactly: `iot_rule_energy_telemetry_to_waste_detector` *(Do not add spaces or change to dashes).*
2. For **Rule description**, enter: `Forward energy telemetry from MQTT topic to Lambda Waste Detector`
3. The **Tags** section can be left blank. Click: **Next**
4. The next page is usually named **Configure SQL statement**.
5. In **SQL version**, choose: `2016-03-23` *(This is usually the default version selected by AWS IoT Console).*
6. In the **SQL statement** box, delete the sample content and paste:
```sql
SELECT * FROM 'home/lab/telemetry'