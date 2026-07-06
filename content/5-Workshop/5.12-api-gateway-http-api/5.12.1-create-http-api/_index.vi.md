---
title : "Tạo HTTP API"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.12.1. </b> "
---

#### Bước 1: Mở API Gateway

1. Kiểm tra Region: `Asia Pacific (Singapore) ap-southeast-1`
2. Tại thanh tìm kiếm AWS Console, nhập: `API Gateway`
3. Chọn dịch vụ: **Amazon API Gateway**
4. Bấm: **Create API**
5. Tìm loại: **HTTP API** và bấm: **Build**
   *(Không chọn: REST API, WebSocket API, hoặc REST API Private. HTTP API hỗ trợ JWT authorizer trực tiếp và phù hợp với kiến trúc serverless).*

#### Bước 2: Nhập thông tin API

- **API name**: `energy-waste-http-api`
- **IP address type**: `IPv4` *(Nếu có lựa chọn Dualstack thì chưa cần chọn).*
- **Integrations**: Hiện tại không thêm integration. Không chọn `energy-virtual-sensor` hoặc `energy-waste-detector` (vì hai Lambda này thuộc luồng IoT). Nếu giao diện có nút **Add integration**, hãy bỏ qua và bấm: **Next**.

#### Bước 3: Configure routes

- Tại trang Configure routes, hiện tại chưa cần nhập route. Bấm: **Next**.

#### Bước 4: Configure stages

- Giữ stage: `$default`
- Đảm bảo: **Auto-deploy**: **On**
  *(Stage $default cho phép gọi API trực tiếp từ URL cơ sở mà không cần thêm /dev hoặc /prod. Khi Auto-deploy bật, thay đổi cấu hình được triển khai tự động).*
- Bấm: **Next**.

#### Bước 5: Review and create

- Kiểm tra các thông tin:
  - **API name**: `energy-waste-http-api`
  - **Protocol type**: `HTTP`
  - **IP address type**: `IPv4`
  - **Stage**: `$default`
  - **Auto-deploy**: `Enabled`
- Bấm: **Create**.

**Kết quả:**
Bạn sẽ thấy trang Overview của `energy-waste-http-api`. Hãy ghi lại **API ID** và **Invoke URL**.

![Tạo HTTP API](/images/5-Workshop/5.12-api-gateway/5.12.1-create-http-api.png)