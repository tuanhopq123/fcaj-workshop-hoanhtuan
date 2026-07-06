---
title : "Cấu hình Build và Biến Môi trường"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.16.3. </b> "
---

#### Bước 1: Chọn Repository và Nhánh triển khai

1. Chọn chính xác kho lưu trữ chứa dự án Next.js của bạn kèm theo nhánh mục tiêu muốn deploy (ví dụ: `main` hoặc `master`).
2. Nhấn **Next**.

#### Bước 2: Cấu hình cài đặt ứng dụng & Biến môi trường

1. Tại trang **App settings**, kiểm tra lại các thiết lập build tự động mà hệ thống vừa nhận diện.
2. Mở rộng phần cấu hình nâng cao **Advanced settings** hoặc mục **Environment variables**.
3. Thêm các biến môi trường thiết yếu phục vụ cho việc vận hành. Hãy dán chuỗi **Invoke URL** của API Gateway đã sao chép ở bước trước vào biến cấu hình API tương ứng.
4. Kiểm tra lại toàn bộ thông tin cấu hình và nhấn **Save and deploy** để kích hoạt tiến trình build tự động.