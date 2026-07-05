---
title : "Cấu hình Environment Variables"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.13.3. </b> "
---

Environment Variables giúp thay đổi tên bảng, phòng mặc định và giới hạn dữ liệu mà không phải sửa mã nguồn. AWS cho phép cấu hình tại **Configuration** -> **Environment variables**. 

#### Thực hiện

1. Chọn: **Configuration** -> **Environment variables**
2. Bấm: **Edit**
3. Thêm bốn biến sau:

**Biến 1**
- Key: `DDB_TABLE`
- Value: `EnergyWasteData`

**Biến 2**
- Key: `DEFAULT_ROOM_ID`
- Value: `lab-01`

**Biến 3**
- Key: `DEFAULT_LIMIT`
- Value: `50`

**Biến 4**
- Key: `REPORTS_PK`
- Value: `REPORTS`

![Thêm Environment Variables](/images/5-Workshop/5.13-lambda-api-handler/5.13.3-add-env.png)

4. Bấm: **Save**

Sau khi save:

![Đã lưu Environment Variables](/images/5-Workshop/5.13-lambda-api-handler/5.13.3-env-saved.png)