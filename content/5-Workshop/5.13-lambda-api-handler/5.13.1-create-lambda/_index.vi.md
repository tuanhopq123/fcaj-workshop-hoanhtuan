---
title : "Tạo Lambda API Handler"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.13.1. </b> "
---

#### Bước 1: Mở Lambda

1. Kiểm tra Region ở góc trên bên phải: `Asia Pacific (Singapore) ap-southeast-1`
2. Tại ô tìm kiếm AWS Console, nhập: `Lambda`
3. Chọn dịch vụ: **Lambda**
4. Trong menu bên trái, chọn: **Functions**
5. Bấm: **Create function**

#### Bước 2: Cấu hình function

- Chọn: **Author from scratch**
- Nhập các thông tin sau:
  - **Function name**: `energy-api-handler`
  - **Runtime**: `Python 3.14`
- Giữ nguyên các cấu hình mặc định:
  - Durable execution: **Off**
  - EC2 capacity provider: **Off**
  - ARM64 architecture: **Off**
  - Custom execution role: **Off** *(AWS sẽ tự động tạo một role cơ bản)*.
  - Function URL: **Off**
  - VPC: **Off**
- Bấm: **Create function**

![Tạo Lambda API Handler](/images/5-Workshop/5.13-lambda-api-handler/5.13.1-create-lambda.png)