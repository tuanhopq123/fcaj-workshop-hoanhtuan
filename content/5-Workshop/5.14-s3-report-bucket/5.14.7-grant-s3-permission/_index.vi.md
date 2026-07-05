---
title : "Cấp quyền s3:GetObject cho API Handler"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.14.7. </b> "
---

`energy-api-handler` chỉ cần tải object theo một `objectKey` đã lấy từ metadata trong DynamoDB. Vì vậy, quyền cần cấp là: `s3:GetObject`.
*(Không cần cấp `s3:PutObject`, `s3:DeleteObject`, `s3:ListAllMyBuckets`, hay `s3:*`. AWS xác định `s3:GetObject` là quyền bắt buộc để đọc một object không chỉ định version ID).*

#### Mở IAM Role

1. Trong Lambda `energy-api-handler`, chọn: **Configuration** -> **Permissions**.
2. Tại **Execution role**, bấm tên role màu xanh. Tên gần giống: `energy-api-handler-role-xxxxxxxx`.
3. IAM sẽ được mở trong một tab mới.

#### Tạo inline policy riêng cho S3

1. Bấm: **Add permissions** -> **Create inline policy**.
2. Chọn tab: **JSON**.
3. Xóa đoạn JSON mẫu.
4. Dán policy sau:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadGeneratedEnergyReports",
      "Effect": "Allow",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::energy-waste-report-347685737655-ap-southeast-1/*"
    }
  ]
}

*Lưu ý phần `/*` ở cuối ARN (`arn:aws:s3:::energy-waste-report-347685737655-ap-southeast-1/*`). Nó đại diện cho các object bên trong bucket. Execution role là cơ chế cấp quyền cho Lambda truy cập tài nguyên AWS khác; vì vậy quyền đọc S3 phải nằm trong role của energy-api-handler.*

5. Bấm: **Next**.
6. Tại **Policy name**, nhập: `energy-api-handler-s3-read-policy`
7. Bấm: **Create policy**.

#### Kết quả đúng
Execution role phải có đủ ba policy:
1. `AWSLambdaBasicExecutionRole`
2. `energy-api-handler-dynamodb-read-policy`
3. `energy-api-handler-s3-read-policy`

![Cấp quyền S3 cho API Handler](/images/5-Workshop/5.14-s3-report/5.14.7-iam-s3.png)