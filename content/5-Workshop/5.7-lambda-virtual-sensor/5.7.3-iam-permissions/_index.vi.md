---
title: "5.7.3. Cấp Quyền IAM Publish đến AWS IoT Core"
date: 2026-07-05
weight: 3
---

Để Lambda có thể gửi dữ liệu đi, Execution Role đi kèm cần phải được bổ sung quyền `iot:Publish` đến chính xác topic đích.

1. Tại tab **Configuration**, chọn mục **Permissions** từ menu bên trái.
2. Tại phần **Execution role**, click vào đường dẫn liên kết màu xanh của Role dạng: `energy-virtual-sensor-role-xxxxxx` để chuyển hướng sang trang quản lý IAM Role.
3. Trong trang chi tiết của IAM Role, bấm nút **Add permissions** và chọn **Create inline policy** *(Tham chiếu tệp `03-iam-iot-publish-policy.png`)*.
   ![Giao diện đính kèm chính sách IAM](/images/5-Workshop/5.7-lambda-virtual-sensor/03-iam-iot-publish-policy.png)
4. Chuyển sang tab **JSON**, xóa toàn bộ mã mẫu hiện tại và dán đoạn chính sách bảo mật sau:

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