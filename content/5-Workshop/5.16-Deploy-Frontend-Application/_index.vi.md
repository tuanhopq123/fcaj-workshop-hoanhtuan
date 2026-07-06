---
title: "5.16. Triển khai Ứng dụng Frontend"
date: 2026-07-06T20:30:00+07:00
draft: false
weight: 560
description: "Tổng quan quy trình triển khai ứng dụng frontend Next.js bằng AWS Amplify và tích hợp các API backend."
---

AWS Amplify Hosting được sử dụng để tự động triển khai, bảo mật và mở rộng ứng dụng frontend, cho phép người dùng tương tác với các số liệu đo lường nhà thông minh theo thời gian thực một cách mượt mà.

Trong mục này, chúng ta sẽ thực hiện sáu bước chính:

### 1. [Lấy đường dẫn Invoke URL của API Gateway](5.16.1-Get-API-Gateway-Invoke-URL/)
Hướng dẫn truy cập bảng điều khiển API Gateway và sao chép endpoint của stage triển khai mặc định để tích hợp vào frontend.

### 2. [Khởi tạo Ứng dụng trên AWS Amplify](5.16.2-Initialize-Amplify-Application/)
Hướng dẫn từng bước kết nối nhánh kho lưu trữ (repository) từ nhà cung cấp mã nguồn Git với nền tảng AWS Amplify Hosting.

### 3. [Cấu hình Build và Biến Môi trường](5.16.3-Configure-App-Build-and-Environment-Variables/)
Hướng dẫn cấu hình các bước build nâng cao và cấu hình các biến môi trường chứa URL API backend một cách an toàn.

### 4. [Cấu hình CORS và Cấp quyền Origin](5.16.4-Configure-CORS-and-Security-Origins/)
Hướng dẫn cấp quyền chia sẻ tài nguyên giữa các nguồn khác nhau (CORS) trên hạ tầng backend cho tên miền production vừa được tạo ra từ Amplify.

### 5. [Truy cập Giao diện Đăng nhập đã Triển khai](5.16.5-Access-Hosted-Login-Interface/)
Kiểm tra đường dẫn URL công khai của ứng dụng sau khi deploy và xác thực cấu trúc giao diện đăng nhập được tích hợp với Cognito.

### 6. [Kiểm tra và Xác thực Hệ thống trên Dashboard](5.16.6-System-Dashboard-Verification/)
Các bước kiểm tra vận hành cuối cùng nhằm đảm bảo luồng dữ liệu đăng nhập và các biểu đồ đo lường hiển thị chính xác trên giao diện dashboard chính.