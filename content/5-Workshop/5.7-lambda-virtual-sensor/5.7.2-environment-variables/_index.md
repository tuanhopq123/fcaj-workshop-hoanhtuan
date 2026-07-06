---
title: "5.7.2. Configure Environment Variables"
date: 2026-07-05
weight: 2
---

Using Environment Variables allows the source code to dynamically retrieve configurations (such as the IoT Topic or Room ID) without hard-coding them directly into the script.

1. In the `energy-virtual-sensor` Lambda management interface, navigate to the **Configuration** tab.
2. Select **Environment variables** from the left menu, then click **Edit**.
3. Add the following two core environment variables *(Reference: `02-environment-variables-virtual-sensor1.png`)*:
   ![Cấu hình giá trị biến môi trường](/images/5-Workshop/5.7-lambda-virtual-sensor/02-environment-variables-virtual-sensor1.png)
   * **Variable 1**: `Key = IOT_TOPIC` | `Value = home/lab/telemetry`
   * **Variable 2**: `Key = DEFAULT_ROOM_ID` | `Value = lab-01`
4. Click **Save** to apply the changes. The system will display a success status update *(Reference: `02-environment-variables-virtual-sensor2.png`)*.
![Danh sách biến môi trường đã lưu](/images/5-Workshop/5.7-lambda-virtual-sensor/02-environment-variables-virtual-sensor2.png)