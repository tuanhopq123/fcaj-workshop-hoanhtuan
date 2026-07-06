---
title : "Cấu hình CORS và Cấp quyền Origin"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.16.4. </b> "
---

#### Bước 1: Lấy Tên miền (Domain) của Ứng dụng Amplify

1. Chờ cho quy trình build và deploy trên AWS Amplify hoàn tất thành công.
2. Sao chép đường dẫn URL công khai của trang web vừa được sinh ra từ bảng điều khiển Amplify Hosting (ví dụ: `https://main.d2ppdnlr5ik3e8.amplifyapp.com`).

#### Bước 2: Cập nhật CORS trong API Gateway / Lambda

1. Quay trở lại bảng điều khiển cấu hình của các tài nguyên Backend (API Gateway hoặc các hàm Lambda xử lý luồng dữ liệu).
2. Tìm đến tab cấu hình **CORS** hoặc thiết lập bảo mật.
3. Tại mục **Access-Control-Allow-Origin** (Allow origins), thêm tên miền của ứng dụng Amplify bạn vừa sao chép vào để cấp quyền chia sẻ tài nguyên giữa các nguồn khác nhau.
4. Lưu cấu hình nhằm đảm bảo Frontend có thể gửi yêu cầu và nhận dữ liệu từ Backend một cách an toàn mà không bị chặn bởi cơ chế CORS.