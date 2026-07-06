---
title : "Gắn Lambda Action"
date : 2026-07-05 
weight : 3
chapter : false
pre : " <b> 5.8.3 </b> "
---

1. Trang tiếp theo thường có tên: **Attach rule actions**[cite: 11].
2. Trong phần **Rule actions**, bấm: **Add action** *(Nếu giao diện đã có sẵn một ô chọn action, không cần bấm Add action)*[cite: 11].
3. Tại **Action type** hoặc **Choose an action**, chọn: **Lambda** *(Tên trong giao diện có thể hiển thị là `Lambda` hoặc `Send a message to a Lambda function`)*[cite: 11].
4. Tại **Lambda function**, chọn: `energy-waste-detector`[cite: 11].
   + *Không chọn `energy-virtual-sensor`*[cite: 11].
5. Nếu có mục **Version or alias**, để mặc định: `$LATEST` (hoặc để trống nếu Console không bắt buộc)[cite: 11].
6. Không tạo IAM execution role cho action này[cite: 11].
7. Bấm: **Next**[cite: 11].
8. Bấm: **Create**[cite: 11].

![Review](/images/5-Workshop/5.8-AWS-IoT-Core/rule2.png)

Thông báo tạo thành công[cite: 11]:

![Success](/images/5-Workshop/5.8-AWS-IoT-Core/rule3.png)

#### Kiểm tra quyền Lambda được AWS IoT thêm tự động

1. Mở tab AWS Console mới[cite: 11].
2. Vào: **Lambda → Functions → energy-waste-detector**[cite: 11].
3. Chọn: **Configuration → Permissions**[cite: 11].
4. Tìm: **Resource-based policy statements**. Mở rộng policy nếu cần[cite: 11].
5. Bạn cần thấy một statement có nội dung gần giống[cite: 11]:
   + **Principal:** `iot.amazonaws.com`
   + **Action:** `lambda:InvokeFunction`
6. Source ARN phải liên quan đến rule: `arn:aws:iot:ap-southeast-1:347685737655:rule/iot_rule_energy_telemetry_to_waste_detector`[cite: 11].

{{% notice note %}}
Đây không phải inline policy của execution role. Đây là resource-based policy của Lambda[cite: 11].
{{% /notice %}}

![Permissions](/images/5-Workshop/5.8-AWS-IoT-Core/01-iot-rule-details.png)