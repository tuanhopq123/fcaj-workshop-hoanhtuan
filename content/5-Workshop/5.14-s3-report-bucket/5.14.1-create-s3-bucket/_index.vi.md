---
title : "Tạo S3 Report Bucket"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.14.1. </b> "
---

#### Bước 1: Mở Amazon S3

1. Kiểm tra góc trên bên phải đang là: **Asia Pacific (Singapore)**
2. Tại thanh tìm kiếm AWS Console, nhập: `S3`
3. Chọn: **Amazon S3**
4. Trong menu bên trái, chọn: **General purpose buckets** *(Giao diện khác có thể chỉ hiển thị "Buckets")*.
5. Bấm: **Create bucket**

#### Bước 2: Chọn loại bucket

- Tại **Bucket type**, chọn: `General purpose`
- *(Không chọn directory bucket).*

#### Bước 3: Nhập tên bucket

- Tại **Bucket name**, nhập chính xác: `energy-waste-report-347685737655-ap-southeast-1`

*Lưu ý: Tên S3 general purpose bucket nằm trong namespace dùng chung nên phải là duy nhất. Việc ghép Account ID và Region giúp giảm khả năng trùng tên. Nếu AWS báo lỗi "Bucket with the same name already exists", hãy kiểm tra trước xem bucket đó có nằm trong chính tài khoản của bạn hay không. Không tự ý tạo thêm nhiều bucket gần giống nhau.*

#### Bước 4: Chọn Region

- Tại **AWS Region**, chọn: `Asia Pacific (Singapore) ap-southeast-1`
- *(Không chọn Bangkok, Tokyo hoặc Virginia).*