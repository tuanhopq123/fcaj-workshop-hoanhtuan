---
title : "Cập nhật API Gateway CORS"
date : 2026-07-05
weight : 11
chapter : false
pre : " <b> 5.16.11 </b> "
---

Vào:

**API Gateway → APIs → energy-waste-http-api → CORS → Edit**

Cấu hình:

**Allow origins**
```
http://localhost:3000
https://main.d2ppdnlr5ik3e8.amplifyapp.com
```
Không thêm dấu `/` cuối domain.

**Allow headers**
```
authorization
content-type
```

**Allow methods**
```
GET
OPTIONS
```

**Expose headers**: để trống.

**Max age**: `300`

**Allow credentials**: `Off`

Bấm **Save**.

![Cấu hình CORS trong API Gateway](/images/5-Workshop/5.16/pic9.png)

## Kết quả có được

Sau khi frontend đã deploy trên Amplify và CORS đã cấu hình trên API Gateway, dashboard tải dữ liệu thực tế từ DynamoDB thông qua backend Lambda/API Gateway sau khi đăng nhập bằng Cognito.

![Kết quả Energy Monitoring Dashboard](/images/5-Workshop/5.16/pic11.png)

![Kết quả cảnh báo lãng phí và báo cáo](/images/5-Workshop/5.16/pic12.png)
