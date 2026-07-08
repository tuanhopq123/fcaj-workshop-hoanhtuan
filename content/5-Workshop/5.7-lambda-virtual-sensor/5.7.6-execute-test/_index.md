---
title: "5.7.6. Execute Test and Verify Results"
date: 2026-07-05
weight: 6
---

1. In the Test event dropdown, select the newly created event: `manual_force_waste_test`.
2. Click the **Test** button.
3. The Lambda function will execute. Upon completion, review the **Execution result** tab. Ensure that the function execution succeeds with `statusCode: 200`, returns `"message": "Telemetry published successfully"`, and captures `"scenario": "waste"` to confirm accurate behavior.
     ![Kết quả kiểm tra hàm Lambda thành công](/images/5-Workshop/5.7-lambda-virtual-sensor/06-ket-qua-test-virtual-sensor.png)