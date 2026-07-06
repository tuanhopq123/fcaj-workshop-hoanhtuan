---
title : "Kiểm tra quyền API Gateway trên Lambda"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b> 5.13.9. </b> "
---

#### Thực hiện

1. Vào: **Lambda** -> `energy-api-handler` -> **Configuration** -> **Permissions**.
2. Tìm mục: **Resource-based policy statements**.
3. Bạn cần thấy một statement có nội dung gần giống như sau:
   - **Principal**: `apigateway.amazonaws.com`
   - **Action**: `lambda:InvokeFunction`
   - **Source ARN**: `arn:aws:execute-api:ap-southeast-1:347685737655:<API-ID>/*`

*Lưu ý: Không chỉnh sửa policy này nếu API Gateway Console đã tự động tạo thành công.*

![Kiểm tra Resource-based Policy](/images/5-Workshop/5.13-lambda-api-handler/5.13.9-resource-policy.png)