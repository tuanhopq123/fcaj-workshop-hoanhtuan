---
title : "Tạo Item Room Mẫu"
date : 2026-07-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

Bây giờ mình tạo 1 item mẫu để chứng minh bảng hoạt động.

1. **Mở Explore table items**
   * Vào **DynamoDB** -> **Tables** -> `EnergyWasteData`.
   * Chọn **Explore table items**.

![Trang Settings của bảng EnergyWasteData - nút Explore table items](/images/5-Workshop/5.4-dynamodb/pic6.png)

2. **Tạo item bằng JSON view**
   * Bấm **Create item**.
   * Nếu giao diện có nút chuyển đổi, chọn **JSON view**.
   * Dán item này:

```json
{
  "PK": {
    "S": "ROOM#lab-01"
  },
  "SK": {
    "S": "PROFILE"
  },
  "entityType": {
    "S": "Room"
  },
  "roomId": {
    "S": "lab-01"
  },
  "roomName": {
    "S": "Smart Home Lab"
  },
  "powerThresholdW": {
    "N": "120"
  },
  "createdBy": {
    "S": "manual-console"
  }
}
```

![Edit item - JSON view](/images/5-Workshop/5.4-dynamodb/pic1.png)

3. **Kiểm tra item đã được lưu**
   * Bấm **Save**.
   * Chạy **Scan** để xác nhận item xuất hiện trong kết quả.

![Item đã lưu thành công - kết quả Explore items](/images/5-Workshop/5.4-dynamodb/pic7.png)
