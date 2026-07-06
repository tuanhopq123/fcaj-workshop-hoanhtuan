---
title: "5.6.3 IAM permission"
weight: 1
---

# 5.6.3 Cấu hình phân quyền IAM cho Lambda

Mặc định, một hàm AWS Lambda sẽ không có quyền ghi dữ liệu vào DynamoDB hay gửi thông báo tới Amazon SNS. Chúng ta cần gán một chính sách bảo mật nội bộ (inline policy) để cấp các đặc quyền vận hành này.

### Các bước thực hiện:

1. Tại giao diện hàm **energy-waste-detector**, di chuyển tới tab **Configuration** -> chọn mục **Permissions**.
2. Tại phân đoạn **Execution role**, nhấp chọn vào liên kết tên role hiện tại (tên sẽ có định dạng tương tự như `energy-waste-detector-role-pmsoahv7`). Hệ thống sẽ tự động mở tab mới chuyển sang bảng điều khiển IAM Role.
3. Trong giao diện cấu hình IAM Role, nhấp chọn nút **Add permissions** và chọn **Create inline policy** từ menu thả xuống.
4. Chuyển đổi chế độ biên soạn sang tab mã **JSON**.
5. Xóa sạch toàn bộ nội dung mẫu mặc định hiện có trong khung nhập liệu và dán đoạn chính sách phân quyền sau:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "WriteEnergyWasteData",
      "Effect": "Allow",
      "Action": [
        "dynamodb:PutItem"
      ],
      "Resource": "arn:aws:dynamodb:ap-southeast-1:347685737655:table/EnergyWasteData"
    },
    {
      "Sid": "PublishEnergyWasteAlert",
      "Effect": "Allow",
      "Action": [
        "sns:Publish"
      ],
      "Resource": "arn:aws:sns:ap-southeast-1:347685737655:energy-waste-alert-topic"
    }
  ]
}