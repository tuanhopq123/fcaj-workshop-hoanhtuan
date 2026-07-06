---
title: "5.7.3. Grant IAM Permissions to Publish to AWS IoT Core"
date: 2026-07-05
weight: 3
---

To enable the Lambda function to send telemetry data, its associated Execution Role must be granted permissions to `iot:Publish` to the exact target topic.

1. In the **Configuration** tab, select the **Permissions** section from the left menu.
2. Under **Execution role**, click the blue hyperlink of the generated role (e.g., `energy-virtual-sensor-role-xxxxxx`) to open the IAM Role management console.
3. On the IAM Role details page, click **Add permissions** and select **Create inline policy** *(Reference: `03-iam-iot-publish-policy.png`)*.
   ![Giao diện đính kèm chính sách IAM](/images/5-Workshop/5.7-lambda-virtual-sensor/03-iam-iot-publish-policy.png)
4. Switch to the **JSON** tab, clear the existing default template, and paste the following security policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublishTelemetryToIoTCore",
      "Effect": "Allow",
      "Action": [
        "iot:Publish"
      ],
      "Resource": "arn:aws:iot:ap-southeast-1:347685737655:topic/home/lab/telemetry"
    }
  ]
}