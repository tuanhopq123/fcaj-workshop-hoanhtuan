---
title: "5.7.5. Create a Test Event"
date: 2026-07-05
weight: 5
---

To verify the energy waste logic, we will create a custom test event that explicitly passes the `forceWaste` flag.

1. Navigate to the **Test** tab inside the Lambda function interface and select **Create new event**.
2. Configure the Test Event details as follows *(Reference: `05-test-event-force-waste.png`)*:
   ![Tạo test event mới](/images/5-Workshop/5.7-lambda-virtual-sensor/05-test-event-force-waste.png)
   * **Event sharing settings**: Select `Private`.
   * **Event name**: Enter `manual_force_waste_test`.
   * **Event JSON**: Replace the default payload structure with the following block:
```json
{
  "source": "manual-test",
  "forceWaste": true
}
