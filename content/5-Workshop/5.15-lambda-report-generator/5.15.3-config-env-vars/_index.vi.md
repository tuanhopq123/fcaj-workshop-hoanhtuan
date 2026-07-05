---
title : "Cấu hình Environment Variables"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.15.3. </b> "
---

Lambda cần biết tên bảng DynamoDB, bucket S3, phòng mặc định và prefix lưu báo cáo để hoạt động chính xác.

#### Bước 1: Mở Environment variables

1. Trong hàm Lambda `energy-report-generator`.
2. Chọn tab: **Configuration**
3. Trong menu bên trái, chọn: **Environment variables**
4. Bấm: **Edit**

#### Bước 2: Thêm các biến môi trường

Bấm **Add environment variable** để thêm lần lượt các biến sau:

1. **DDB_TABLE**
   - Key: `DDB_TABLE`
   - Value: `EnergyWasteData`
2. **REPORT_BUCKET**
   - Key: `REPORT_BUCKET`
   - Value: `energy-waste-report-347685737655-ap-southeast-1`
   - *(Lưu ý: Không nhập `s3://...`, giá trị chỉ là tên bucket).*
3. **REPORTS_PK**
   - Key: `REPORTS_PK`
   - Value: `REPORTS`
4. **DEFAULT_ROOM_ID**
   - Key: `DEFAULT_ROOM_ID`
   - Value: `lab-01`
5. **REPORT_PREFIX**
   - Key: `REPORT_PREFIX`
   - Value: `reports`

#### Bước 3: Lưu cấu hình

Kiểm tra lại xem đã đủ 5 biến chưa, sau đó bấm **Save**.

*Lưu ý bảo mật: Không đặt các thông tin nhạy cảm như AWS access key, JWT, Cognito password, hay Client secret trong Environment Variables. Lambda sẽ tự động sử dụng AWS credentials tạm thời từ execution role.*

![Cấu hình Environment Variables](/images/5-Workshop/5.15-lambda-report/5.15.3-env-vars.png)