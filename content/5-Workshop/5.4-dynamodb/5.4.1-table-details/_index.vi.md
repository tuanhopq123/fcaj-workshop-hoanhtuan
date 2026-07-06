---
title: "5.4.1 Cấu hình Table Details & Settings"
weight: 1
description: "Thiết lập các thông số chính như Partition key, Sort key và Capacity mode cho DynamoDB."
---

# 5.4.1 Cấu hình Table details

Tại giao diện khởi tạo bảng, bạn tiến hành điền chính xác các thông tin cấu hình cốt lõi dưới đây[cite: 1]:

### 1. Thông tin chi tiết của Bảng (Table details)
* **Table name:** `EnergyWasteData`[cite: 1]
* **Partition key:** `PK` (Kiểu dữ liệu: **String**)[cite: 1]
* **Sort key - optional:** `SK` (Kiểu dữ liệu: **String**)[cite: 1]

> ⚠️ **LƯU Ý QUAN TRỌNG:** 
> Bạn bắt buộc phải viết hoa chính xác cụm từ **PK** và **SK**[cite: 1]. Tuyệt đối không được viết thành `pk`, `sk`, `roomId`, hay `id`[cite: 1]. Logic xử lý trong mã nguồn Lambda sau này sẽ sử dụng đúng các ký tự viết hoa này để truy vấn[cite: 1].

![Cấu hình Table details](/images/5-Workshop/5.4-dynamodb/dynamodb-open-create-table.png)


---

### 2. Cấu hình cài đặt Bảng (Table settings)

Tiếp tục kéo xuống phía dưới để cấu hình các tùy chọn nâng cao phù hợp cho workshop[cite: 1]:

* Tại mục **Table settings**, chọn **Customize settings**[cite: 1].
* Tại mục **Table class**, chọn **DynamoDB Standard**[cite: 1].
* Tại mục **Read/write capacity settings** ➔ **Capacity mode**, chọn: **On-demand**[cite: 1].

> 💡 **Lý do chọn On-demand:** Dự án demo không cần phải cấu hình dung lượng đọc/ghi (read/write capacity) cố định, giúp giảm bớt các thao tác thiết lập phức tạp và tối ưu cho bài thực hành[cite: 1].

![Cấu hình Chế độ On-demand](/images/5-Workshop/5.4-dynamodb/dynamodb-table-details.png)

### 3. Hoàn tất các thiết lập mặc định khác
* **Secondary indexes:** Không tạo[cite: 1].
* **Encryption:** Giữ nguyên *AWS owned key* hoặc mặc định[cite: 1].
* **Deletion protection:** Tạm thời để trạng thái **Off**[cite: 1].
* **Tags:** Có thể bỏ qua[cite: 1].

Sau khi kiểm tra lại thông tin, bấm nút **Create table**[cite: 1]. Hệ thống sẽ tiến hành khởi tạo và chuyển bảng sang trạng thái **Active**[cite: 1].

![Bảng DynamoDB ở trạng thái Active](/images/5-Workshop/5.4-dynamodb/dynamodb-on-demand-settings.png)