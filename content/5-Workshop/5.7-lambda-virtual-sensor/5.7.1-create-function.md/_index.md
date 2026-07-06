---
title: "5.7.1. Create a Lambda Function"
date: 2026-07-05
weight: 1
---

1. In the AWS Management Console search bar, type `Lambda` and select the **Lambda** service.
2. In the left navigation menu, click **Functions**.
3. Click the **Create function** button *(Reference: `01-tao-lambda-virtual-sensor1.png`)*.
   ![Giao diện Lambda Functions](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda1.png)
4. On the configuration page, configure the basic information as follows:
   * **Authorization method**: Select **Author from scratch**.
   * **Function name**: Enter `energy-virtual-sensor`.
   * **Runtime**: Select **Python 3.14**.
   * **Advanced settings**: Keep the default settings or leave the advanced options unchecked.
5. Review all information carefully *(Reference: `01-tao-lambda-virtual-sensor2.png`)* and click 
   ![Cấu hình thông tin cơ bản Lambda function](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda2.png)
   **Create function**. 
6. Once successfully created, the system will direct you to the function management interface *(Reference: `01-tao-lambda1.png` and `01-tao-lambda2.png`)*.
   ![Tổng quan hàm Lambda sau khi tạo](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda-virtual-sensor1.png)
   ![Thuộc tính Runtime và mã hash hàm Lambda](/images/5-Workshop/5.7-lambda-virtual-sensor/01-tao-lambda-virtual-sensor2.png)