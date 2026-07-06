---
title : "Lấy đường dẫn Invoke URL của API Gateway"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.16.1. </b> "
---

#### Bước 1: Mở API Gateway Console

1. Tại thanh tìm kiếm của AWS Console, nhập: `API Gateway`
2. Chọn dịch vụ **API Gateway**.
3. Trong danh sách các API, nhấn chọn HTTP API đã tạo cho dự án: `energy-waste-http-api`.

#### Bước 2: Sao chép đường dẫn Invoke URL

1. Ở danh mục điều hướng bên trái, tìm đến phần **Deploy** và chọn **Stages**.
2. Chọn stage **$default** từ danh sách các stage hiện có.
3. Tại khu vực **Stage details**, tìm mục **Invoke URL**.
4. Sao chép toàn bộ chuỗi URL hiển thị tại đây. Chuỗi này sẽ được sử dụng làm Base URL để ứng dụng Frontend gọi các API xử lý phía Backend.

![API Gateway Invoke URL](/images/5-Workshop/5.16/API-Gateway-Invoke-URL.png)