---
title : "Kiểm tra file trong S3"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.15.7. </b> "
---

#### Bước 1: Mở S3 Bucket

1. Mở dịch vụ **Amazon S3**.
2. Chọn bucket: `energy-waste-report-347685737655-ap-southeast-1`

#### Bước 2: Mở prefix báo cáo

1. Trong tab **Objects**, mở thư mục: `reports`
2. Tiếp tục mở thư mục: `2026-07-03`
3. Kiểm tra xem có file này không: `energy-report-lab-01-2026-07-03.json`
4. Đường dẫn đầy đủ phải là: `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

#### Bước 3: Kiểm tra object

Bấm vào file và kiểm tra các thông số sau:
- **Type**: `json`
- **Content type**: `application/json`
- **Encryption**: `SSE-S3`
- Kích thước file phải lớn hơn **0 byte**.

*Lưu ý bảo mật:*
- Không bấm nút `Make public`.
- Không tắt tính năng `Block all public access`.

![Kiểm tra file trong S3](/images/5-Workshop/5.15-lambda-report/5.15.7-s3-file.png)