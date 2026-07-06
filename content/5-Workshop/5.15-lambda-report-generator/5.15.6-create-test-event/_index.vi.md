---
title : "Tạo Test Event"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.15.6. </b> "
---

Dữ liệu hiện tại của hệ thống được tạo vào ngày `2026-07-03`. Vì vậy chúng ta sẽ sử dụng ngày này để kiểm tra. 

*Lưu ý: Nếu item DynamoDB của bạn có ngày khác, hãy thay `reportDate` bằng đúng ngày xuất hiện trong sort key `TELEMETRY#...` của bạn.*

#### Bước 1: Mở phần Test

1. Trong hàm Lambda `energy-report-generator`.
2. Chọn tab: **Test**.
3. Chọn: **Create new event**.

#### Bước 2: Nhập Test Event

1. Tại **Event name**, nhập: `manual_generate_report_2026_07_03`
2. Dán đoạn JSON sau vào khung mã:

{
  "source": "manual-test",
  "reportDate": "2026-07-03",
  "roomId": "lab-01"
}

3. Bấm nút **Save**.
4. Sau đó bấm nút **Test**.

#### Kết quả đúng

Phần **Execution result** phải hiển thị trạng thái: `Succeeded`

Phần **Response** phải có chứa các giá trị sau:
- `statusCode` = `200`
- `success` = `true`
- `reportDate` = `2026-07-03`
- `roomId` = `lab-01`
- `bucket` = `energy-waste-report-347685737655-ap-southeast-1`
- `objectKey` phải gần giống định dạng: `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

Phần `summary` phải có đầy đủ các trường:
- `telemetryCount`
- `alertCount`
- `wasteCount`
- `totalEnergyKwh`
- `averagePowerW`
- `maxPowerW`

**Xử lý sự cố:**
Nếu kết quả trả về là `"telemetryCount": 0`, hãy kiểm tra lại sort key của dữ liệu trong DynamoDB. Ví dụ, nếu sort key của bạn là `TELEMETRY#2026-07-02T...`, thì bạn cần đổi test event thành ngày tương ứng:

{
  "source": "manual-test",
  "reportDate": "2026-07-02",
  "roomId": "lab-01"
}

![Tạo Test Event](/images/5-Workshop/5.15-lambda-report/5.15.6-test-event.png)