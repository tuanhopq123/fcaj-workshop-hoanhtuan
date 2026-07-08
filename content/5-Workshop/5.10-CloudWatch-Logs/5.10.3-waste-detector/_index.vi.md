---
title : "Kiểm tra Waste Detector Logs"
date : 2026-07-05
weight : 3
chapter : false
pre : " <b> 5.10.3 </b> "
---

1. Quay lại: **CloudWatch → Logs → Log groups**.
2. Chọn: `/aws/lambda/energy-waste-detector`.
3. Chọn log stream có **Last event time** mới nhất. Chọn khoảng thời gian: **Last 1 hour** hoặc **Last 3 hours**.
4. Trong ô filter, nhập: `Received event`.
5. Bạn cần thấy dữ liệu đầu vào có các trường tương tự: `sensorId`, `roomId`, `timestamp`, `deviceStatus`, `occupancy`, `powerW`.
6. Sau đó tìm các dòng tương đương:
   * `Telemetry stored in DynamoDB`.
   * (Nếu thỏa điều kiện lãng phí): `Alert stored in DynamoDB` và `Alert email published to SNS`.

{{% notice note %}}
Do payload sử dụng `forceWaste: false`, dữ liệu cảm biến được tạo ngẫu nhiên và không phải lúc nào cũng thỏa điều kiện cảnh báo. Nếu không có dòng ALERT và không có email gửi thì vẫn là bình thường.
{{% /notice %}}

![Waste Detector Logs Details](/images/5-Workshop/5.10-CloudWatch/03-waste-detector-logs1.png)