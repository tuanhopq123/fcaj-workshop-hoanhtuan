---
title : "Kiểm tra Block Public Access"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.14.4. </b> "
---

#### Bước 1: Mở Bucket

1. Bấm vào bucket: `energy-waste-report-347685737655-ap-southeast-1`
2. Chọn tab: **Permissions**

#### Bước 2: Kiểm tra các thiết lập truy cập

1. Tìm phần: **Block public access (bucket settings)**.
2. Kiểm tra trạng thái: **Block all public access: On**
3. Tìm phần: **Bucket policy**. Giữ ở trạng thái không có public bucket policy.
4. Tìm phần: **Access control list (ACL)**. Phải thể hiện ACL đã bị vô hiệu hóa hoặc Object Ownership đang là **Bucket owner enforced**.

#### Kết quả đúng

- **Block all public access**: `On`
- **Bucket policy**: Không có public policy
- **ACLs**: `Disabled`

![Kiểm tra Block Public Access](/images/5-Workshop/5.14-s3-report/5.14.4-public-access.png)