---
title : "Cấu hình mã hóa và Tạo Bucket"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.14.3. </b> "
---

#### Bước 1: Cấu hình mã hóa (Default encryption)

1. Tại phần **Default encryption**, chọn hoặc giữ thiết lập:
   - **Server-side encryption with Amazon S3 managed keys (SSE-S3)**
2. **Không chọn**: `AWS Key Management Service key (SSE-KMS)` vì project chưa cần customer-managed KMS key.

*Lưu ý: Amazon S3 hiện tự động mã hóa object bằng SSE-S3 theo mặc định. Bạn vẫn nên kiểm tra trên Console để bảo đảm bucket đang dùng SSE-S3 đúng thiết kế. Nếu có phần liên quan đến **S3 Bucket Key** thì không cần cấu hình vì Bucket Key chủ yếu liên quan đến SSE-KMS.*

![Cấu hình mã hóa](/images/5-Workshop/5.14-s3-report/5.14.3-encryption.png)

#### Bước 2: Cấu hình Advanced settings

1. Giữ **Object Lock**: **Disable**

*Lưu ý: Không bật Object Lock vì project không cần cơ chế chống xóa bắt buộc và Object Lock đi kèm yêu cầu phải bật versioning.*

![Cấu hình Object Lock](/images/5-Workshop/5.14-s3-report/5.14.3-object-lock.png)

#### Bước 3: Kiểm tra và Tạo bucket

1. Kiểm tra lần cuối các thông số:
   - **Bucket name**: `energy-waste-report-347685737655-ap-southeast-1`
   - **Region**: `ap-southeast-1`
   - **Object Ownership**: `Bucket owner enforced`
   - **Block all public access**: `On`
   - **Bucket Versioning**: `Disabled`
   - **Default encryption**: `SSE-S3`
   - **Object Lock**: `Disabled`

2. Bấm nút: **Create bucket**.
3. Chờ thông báo tạo thành công. *(AWS Console sẽ tạo bucket sau khi bạn hoàn tất các thiết lập trên và bấm Create bucket).*

![Kiểm tra và Tạo bucket](/images/5-Workshop/5.14-s3-report/5.14.3-create-bucket.png)