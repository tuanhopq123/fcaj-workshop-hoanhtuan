---
title: "5.16. Triển khai ứng dụng Frontend"
date: 2026-07-06T20:30:00+07:00
draft: false
weight: 16
description: "Tổng quan về việc triển khai ứng dụng frontend Next.js bằng AWS Amplify và tích hợp với backend API."
---

AWS Amplify Hosting được sử dụng để deploy, bảo mật và tự động mở rộng ứng dụng frontend, giúp người dùng tương tác với dữ liệu smart home theo thời gian thực một cách liền mạch.

Trong phần này, chúng ta sẽ thực hiện mười một bước chính:

### 1. [Lấy API Gateway Invoke URL](5.16.1-invoke-url/)
Hướng dẫn truy cập console API Gateway và sao chép endpoint của stage mặc định để tích hợp với frontend.

### 2. [Tạo project Next.js](5.16.2-create-nextjs-project/)
Hướng dẫn từng bước khởi tạo ứng dụng Next.js và cài đặt thư viện AWS Amplify.

### 3. [Tạo file .env.local](5.16.3-env-file/)
Hướng dẫn lưu trữ an toàn các giá trị cấu hình Cognito và API Gateway dưới dạng biến môi trường cục bộ.

### 4. [Cấu hình Amplify kết nối Cognito](5.16.4-configure-amplify/)
Hướng dẫn cấu hình thư viện AWS Amplify phía client để frontend có thể xác thực với Cognito User Pool.

### 5. [Cấu hình CSS và Layout](5.16.5-css-layout/)
Thiết lập stylesheet toàn cục và layout gốc của ứng dụng.

### 6. [Tạo hàm lấy JWT và gọi API Gateway](5.16.6-api-helper/)
Xây dựng hàm dùng chung để lấy JWT token từ Cognito và gọi các endpoint API Gateway của backend.

### 7. [Tạo giao diện Dashboard](5.16.7-dashboard-ui/)
Xây dựng component Dashboard chính hiển thị phòng, telemetry, cảnh báo và báo cáo.

### 8. [Tạo trang đăng nhập và kiểm tra phiên Cognito](5.16.8-login-page/)
Triển khai form đăng nhập và logic kiểm tra phiên, hiển thị Dashboard sau khi xác thực thành công.

### 9. [Đưa project lên GitHub](5.16.9-push-github/)
Commit và đẩy source code hoàn chỉnh lên repository GitHub.

### 10. [Tạo ứng dụng AWS Amplify Hosting](5.16.10-amplify-hosting/)
Hướng dẫn từng bước kết nối branch của repository GitHub với AWS Amplify Hosting, cấu hình build settings, biến môi trường và deploy ứng dụng.

### 11. [Cập nhật API Gateway CORS](5.16.11-cors-config/)
Cấp quyền Cross-Origin Resource Sharing (CORS) trên hạ tầng backend cho domain production vừa được Amplify tạo ra, và kiểm tra kết quả cuối cùng.
