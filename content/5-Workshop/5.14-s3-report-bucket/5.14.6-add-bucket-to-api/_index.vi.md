---
title : "Thêm bucket vào Lambda API Handler"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.14.6. </b> "
---

Lambda `energy-api-handler` cần biết bucket nào chứa báo cáo.

#### Thêm Environment Variable

1. Mở: **Lambda** -> **Functions** -> **energy-api-handler**.
2. Chọn: **Configuration** -> **Environment variables**.
3. Bấm: **Edit**.
4. Giữ nguyên bốn biến hiện có:
   - `DDB_TABLE` = `EnergyWasteData`
   - `DEFAULT_ROOM_ID` = `lab-01`
   - `DEFAULT_LIMIT` = `50`
   - `REPORTS_PK` = `REPORTS`
5. Bấm: **Add environment variable**.
6. Nhập thông tin:
   - **Key**: `REPORT_BUCKET`
   - **Value**: `energy-waste-report-347685737655-ap-southeast-1`
7. Bấm: **Save**.

#### Kết quả đúng
Lambda phải có đủ năm biến:
- `DDB_TABLE` = `EnergyWasteData`
- `DEFAULT_ROOM_ID` = `lab-01`
- `DEFAULT_LIMIT` = `50`
- `REPORTS_PK` = `REPORTS`
- `REPORT_BUCKET` = `energy-waste-report-347685737655-ap-southeast-1`

![Thêm bucket vào API Handler](/images/5-Workshop/5.14-s3-report/5.14.6-add-env.png)