---
title : "Cấu hình Table Details"
date : 2026-07-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

1. **Điền Table details**
   * Table name: `EnergyWasteData`
   * Partition key: `PK`, kiểu **String**
   * Sort key: `SK`, kiểu **String**
   * Lưu ý quan trọng: `PK` và `SK` phải viết hoa (không viết `pk`, `sk`, `roomId`, `id`), vì code Lambda sau này sẽ dùng đúng `PK` và `SK`.

![Create table - table details](/images/5-Workshop/5.4-dynamodb/pic3.png)

2. **Tùy chỉnh Table settings**
   * Kéo xuống phần **Table settings** và chọn **Customize settings**.
   * Ở phần **Capacity mode**, chọn **On-demand** (project demo không cần cấu hình read/write capacity cố định, ít thao tác hơn và phù hợp cho workshop).
   * Các phần còn lại để mặc định: không tạo secondary indexes, encryption mặc định, deletion protection để Off, tags có thể bỏ qua.
   * Nếu có phần **Table class**, chọn **DynamoDB Standard**.

![Table settings - Capacity mode](/images/5-Workshop/5.4-dynamodb/pic4.png)

3. **Tạo bảng**
   * Bấm **Create table** và chờ thông báo xác nhận.

![Bảng EnergyWasteData được tạo thành công](/images/5-Workshop/5.4-dynamodb/pic5.png)
