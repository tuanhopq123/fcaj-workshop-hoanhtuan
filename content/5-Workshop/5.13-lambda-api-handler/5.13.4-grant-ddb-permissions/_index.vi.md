---
title : "Cấp quyền đọc DynamoDB"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.13.4. </b> "
---

Lambda cần các quyền:
- `dynamodb:Query`
- `dynamodb:Scan`
- `dynamodb:GetItem`

*Lưu ý: `Query` dùng để đọc telemetry và alert theo partition key; `Scan` dùng để tìm các item `PROFILE` của phòng; `GetItem` dùng để tìm báo cáo theo ngày. DynamoDB `Query` yêu cầu một giá trị partition key và có thể kết hợp điều kiện `begins_with` trên sort key.*

#### Bước 1: Mở execution role

1. Trong Lambda, chọn: **Configuration** -> **Permissions**
2. Tại phần **Execution role**, bấm vào tên role màu xanh. 
   *(Tên thường có dạng: `energy-api-handler-role-xxxxxxxx`)*
3. Trang IAM sẽ mở trong một tab mới.

#### Bước 2: Tạo inline policy

1. Bấm: **Add permissions** -> **Create inline policy**
2. Chọn tab: **JSON**
3. Xóa đoạn JSON mẫu.
4. Dán policy sau:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadEnergyWasteData",
      "Effect": "Allow",
      "Action": [
        "dynamodb:GetItem",
        "dynamodb:Query",
        "dynamodb:Scan"
      ],
      "Resource": [
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData",
        "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData/index/*"
      ]
    }
  ]
}

5. Bấm: **Next**
6. Tại **Policy name**, nhập: `energy-api-handler-dynamodb-read-policy`
7. Bấm: **Create policy**

![Cấp quyền đọc DynamoDB](/images/5-Workshop/5.13-lambda-api-handler/5.13.4-iam-ddb.png)