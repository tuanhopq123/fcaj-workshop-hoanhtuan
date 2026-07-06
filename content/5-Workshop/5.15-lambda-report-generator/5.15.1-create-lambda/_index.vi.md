---
title : "Tạo Lambda Report Generator"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.15.1. </b> "
---

#### Bước 1: Mở Lambda

1. Kiểm tra Region ở góc trên bên phải:
   - **Asia Pacific (Singapore)**
   - `ap-southeast-1`
2. Tại thanh tìm kiếm AWS Console, nhập: `Lambda`
3. Chọn dịch vụ: **Lambda**
4. Trong menu bên trái, chọn: **Functions**
5. Bấm: **Create function**

![Open Lambda](/images/5-Workshop/5.15-lambda-report/5.15.1-step1.png)

#### Bước 2: Nhập cấu hình Lambda

1. Tại trang tạo function, chọn: **Author from scratch**
2. Tại **Function name**, nhập: `energy-report-generator`
3. Tại **Runtime**, chọn: `Python 3.14`
4. Tại **Architecture**, giữ nguyên: `x86_64`
5. Giữ các thiết lập mặc định sau:
   - Durable execution: **Off**
   - EC2 capacity provider: **Off**
   - ARM64 architecture: **Off**
   - Custom execution role: **Off** (Để AWS tự tạo một execution role mới với quyền Lambda cơ bản).
   - Function URL: **Off**
   - VPC: **Off**
6. Bấm: **Create function**

![Configure Lambda](/images/5-Workshop/5.15-lambda-report/5.15.1-step2.png)