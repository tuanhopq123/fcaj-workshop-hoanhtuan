---
title : "Cấu hình Timeout và Memory"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.15.2. </b> "
---

Báo cáo cần đọc nhiều item từ DynamoDB, tổng hợp dữ liệu và tạo file JSON nên cần điều chỉnh tài nguyên:
- **Memory**: 256 MB
- **Timeout**: 30 seconds

#### Bước 1: Mở General configuration

1. Trong hàm Lambda `energy-report-generator`.
2. Chọn tab: **Configuration**
3. Trong menu bên trái, chọn: **General configuration**
4. Bấm: **Edit**

![Open General Config](/images/5-Workshop/5.15-lambda-report/5.15.2-step1.png)

#### Bước 2: Nhập cấu hình

1. Tại **Memory**, nhập: `256 MB`
2. Tại **Timeout**, nhập: `0 min 30 sec`
3. Giữ **Ephemeral storage**: `512 MB`
4. Bấm: **Save**

![Edit Configuration](/images/5-Workshop/5.15-lambda-report/5.15.2-step2.png)

*Lưu ý: Kết quả đúng phải hiển thị Memory: 256 MB, Timeout: 0 min 30 sec, Ephemeral storage: 512 MB. Không cần chụp ảnh riêng nếu thông tin này đã xuất hiện trong ảnh cấu hình Lambda.*