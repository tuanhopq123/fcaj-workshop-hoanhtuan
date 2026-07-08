---
title : "Gắn Lambda Action"
date : 2026-07-05 
weight : 3
chapter : false
pre : " <b> 5.8.3 </b> "
---

1. Trang tiếp theo thường có tên: **Attach rule actions**.
2. Trong phần **Rule actions**, bấm: **Add action** *(Nếu giao diện đã có sẵn một ô chọn action, không cần bấm Add action)*.
3. Tại **Action type** hoặc **Choose an action**, chọn: **Lambda** *(Tên trong giao diện có thể hiển thị là `Lambda` hoặc `Send a message to a Lambda function`)*.
4. Tại **Lambda function**, chọn: `energy-waste-detector`.
   + *Không chọn `energy-virtual-sensor`*.
5. Nếu có mục **Version or alias**, để mặc định: `$LATEST` (hoặc để trống nếu Console không bắt buộc).
6. Không tạo IAM execution role cho action này.
7. Bấm: **Next**.
8. Bấm: **Create**.

![Review](/images/5-Workshop/5.8-AWS-IoT-Core/rule2.png)

Thông báo tạo thành công:

![Success](/images/5-Workshop/5.8-AWS-IoT-Core/rule3.png)

#### Kiểm tra quyền Lambda được AWS IoT thêm tự động

1. Mở tab AWS Console mới.
2. Vào: **Lambda → Functions → energy-waste-detector**.
3. Chọn: **Configuration → Permissions**.
4. Tìm: **Resource-based policy statements**. Mở rộng policy nếu cần.
5. Bạn cần thấy một statement có nội dung gần giống:
   + **Principal:** `iot.amazonaws.com`
   + **Action:** `lambda:InvokeFunction`
6. Source ARN phải liên quan đến rule: `arn:aws:iot:ap-southeast-1:347685737655:rule/iot_rule_energy_telemetry_to_waste_detector`.

{{% notice note %}}
Đây không phải inline policy của execution role. Đây là resource-based policy của Lambda.
{{% /notice %}}

![Permissions](/images/5-Workshop/5.8-AWS-IoT-Core/01-iot-rule-details.png)