---
title : "Kiểm tra Encryption và Versioning"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.14.5. </b> "
---

#### Bước 1: Mở tab Properties

1. Trong bucket, chọn tab: **Properties**

#### Bước 2: Kiểm tra Bucket Versioning

1. Tìm phần: **Bucket Versioning**
2. Kết quả cần thấy là: **Disabled**

#### Bước 3: Kiểm tra Default encryption

1. Tìm phần: **Default encryption**
2. Kết quả cần thấy là:
   - **Server-side encryption with Amazon S3 managed keys**
   - **SSE-S3**

*Lưu ý: Không cần chỉnh sửa gì thêm nếu hai mục này đã hiển thị đúng kết quả.*

![Kiểm tra Encryption và Versioning](/images/5-Workshop/5.14-s3-report/5.14.5-encryption-versioning.png)