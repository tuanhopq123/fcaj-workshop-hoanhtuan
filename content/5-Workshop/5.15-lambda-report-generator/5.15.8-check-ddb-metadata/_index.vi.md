---
title : "Kiểm tra Metadata trong DynamoDB"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.15.8. </b> "
---

#### Bước 1: Mở table

1. Mở dịch vụ **DynamoDB** -> **Tables** -> **EnergyWasteData**.
2. Chọn **Explore table items**.
3. Bạn có thể chọn chế độ **Scan** sau đó bấm **Run**.
4. Hoặc chọn chế độ **Query** và nhập điều kiện: `PK = REPORTS`

#### Bước 2: Tìm metadata

1. Tìm item có chứa cặp khóa sau:
   - `PK` = `REPORTS`
   - `SK` = `REPORT#2026-07-03`
2. Mở item lên và kiểm tra xem đã có đầy đủ các trường sau chưa:
   - `date`
   - `roomId`
   - `bucket`
   - `objectKey`
   - `fileName`
   - `contentType`
   - `generatedAt`
   - `telemetryCount`
   - `alertCount`
   - `wasteCount`
   - `totalEnergyKwh`
   - `averagePowerW`
   - `maxPowerW`

*Kiểm tra chéo: Giá trị của trường `objectKey` bắt buộc phải là:* `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

![Kiểm tra Metadata trong DynamoDB](/images/5-Workshop/5.15-lambda-report/5.15.8-ddb-metadata.png)