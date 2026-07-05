---
title : "Cấp quyền IAM"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.15.4. </b> "
---

Lambda cần các quyền truy cập cụ thể để giao tiếp với các dịch vụ AWS khác:
- `dynamodb:Query`: dùng để đọc TELEMETRY và ALERT.
- `dynamodb:PutItem`: dùng để lưu metadata báo cáo.
- `s3:PutObject`: dùng để lưu file JSON vào S3.
- `AWSLambdaBasicExecutionRole`: dùng để ghi log vào CloudWatch.

#### Bước 1: Mở Execution role

1. Trong hàm Lambda `energy-report-generator`, chọn tab **Configuration**.
2. Trong menu bên trái, chọn **Permissions**.
3. Tại phần **Execution role**, bấm vào tên role màu xanh (ví dụ: `energy-report-generator-role-xxxxxxxx`).
4. Giao diện IAM sẽ được mở trong một tab mới.

#### Bước 2: Kiểm tra quyền CloudWatch

1. Trong phần **Permissions policies**, kiểm tra xem đã có policy `AWSLambdaBasicExecutionRole` chưa.
2. Nếu policy này đã có thì chuyển sang Bước 3.
3. Nếu chưa có, bấm **Add permissions** -> **Attach policies**. Tìm policy `AWSLambdaBasicExecutionRole`, tick chọn và bấm **Add permissions**.

#### Bước 3: Tạo Inline Policy

1. Tại giao diện IAM role, bấm **Add permissions** -> chọn **Create inline policy**.
2. Chọn tab **JSON**.
3. Xóa toàn bộ nội dung mẫu và dán đoạn mã sau:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadAndWriteEnergyReportMetadata",
      "Effect": "Allow",
      "Action": [
        "dynamodb:Query",
        "dynamodb:PutItem"
      ],
      "Resource": [
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData",
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData/index/*"
      ]
    },
    {
      "Sid": "WriteEnergyReportToS3",
      "Effect": "Allow",
      "Action": [
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::energy-waste-report-347685737655-ap-southeast-1/*"
    }
  ]
}
```
1. Bấm Next.

2. Tại Policy name, nhập: energy-report-generator-data-policy

3. Bấm Create policy.

Kiểm tra kết quả: Execution role phải có đủ 2 policy là AWSLambdaBasicExecutionRole và energy-report-generator-data-policy. Tuyệt đối không cấp các quyền quá rộng như dynamodb:*, s3:* hoặc AdministratorAccess.