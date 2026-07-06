---

title : "Test Lambda trực tiếp"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.13.6. </b> "
---

Chúng ta tiến hành kiểm tra độc lập hàm Lambda để xác thực các logic phân tuyến và tương tác cơ sở dữ liệu trước khi kết nối trực tiếp với Amazon API Gateway.

#### Test 1 — GET /rooms

1. Trong hàm Lambda, chọn tab **Test**.
2. Chọn: **Create new event**.
3. Tại **Event name**, nhập: `test_get_rooms`
4. Dán đoạn mã JSON sau:

{
  "version": "2.0",
  "routeKey": "GET /rooms",
  "rawPath": "/rooms",
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/rooms"
    }
  }
}

5. Bấm **Save** sau đó bấm nút **Test**.

**Kết quả đúng:**
- `statusCode` = `200`
- `success` = `true`
- Trong thuộc tính `body` phải trả về mảng chứa thông tin phòng với cấu trúc dữ liệu tương tự: `PK = ROOM#lab-01`, `SK = PROFILE`.
*(Lưu ý: nội dung body được hiển thị dưới dạng chuỗi JSON có chứa các ký tự dấu nháy chéo `\"`; đây là định dạng phản hồi chuẩn và hoàn toàn bình thường của cơ chế Lambda proxy integration).*

#### Test 2 — GET /telemetry

1. Tạo một test event mới với tên: `test_get_telemetry`
2. Dán đoạn mã JSON sau:

{
  "version": "2.0",
  "routeKey": "GET /telemetry",
  "rawPath": "/telemetry",
  "queryStringParameters": {
    "roomId": "lab-01",
    "limit": "20"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/telemetry"
    }
  }
}

3. Bấm nút **Test**.

**Kết quả đúng:**
- `statusCode` = `200`
- `roomId` = `lab-01`
- `count` > `0`
- Trong danh sách `items` phải có các bản ghi chứa sort key bắt đầu bằng: `TELEMETRY#`
*(Lưu ý: DynamoDB sắp xếp các item có cùng partition key theo thứ tự bảng chữ cái của sort key; mã nguồn sử dụng thuộc tính `ScanIndexForward=False` nhằm mục đích truy xuất các dữ liệu mới nhất lên đầu tiên).*

#### Test 3 — GET /alerts

1. Tạo một test event mới với tên: `test_get_alerts`
2. Dán đoạn mã JSON sau:

{
  "version": "2.0",
  "routeKey": "GET /alerts",
  "rawPath": "/alerts",
  "queryStringParameters": {
    "roomId": "lab-01",
    "limit": "20"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/alerts"
    }
  }
}

3. Bấm nút **Test**.

**Kết quả đúng:**
- `statusCode` = `200`
- `roomId` = `lab-01`
- Trong danh sách `items` phải có chứa các sort key bắt đầu bằng: `ALERT#`

#### Test 4 — GET /reports

1. Tạo một test event mới với tên: `test_get_reports`
2. Dán đoạn mã JSON sau:

{
  "version": "2.0",
  "routeKey": "GET /reports",
  "rawPath": "/reports",
  "queryStringParameters": {
    "limit": "20"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/reports"
    }
  }
}

3. Bấm nút **Test**.

**Kết quả dự kiến ở giai đoạn hiện tại:**
- `statusCode` = `200`
- `count` = `0`
- `message` = `Chưa có báo cáo.`
*(Lưu ý: Kết quả này hoàn toàn chính xác và không phải lỗi hệ thống, lý do là phân hệ Report Generator hiện chưa được cấu hình và triển khai).*

#### Test 5 — GET /reports/{date}

1. Tạo một test event mới với tên: `test_get_report_by_date`
2. Dán đoạn mã JSON sau:

{
  "version": "2.0",
  "routeKey": "GET /reports/{date}",
  "rawPath": "/reports/2026-07-03",
  "pathParameters": {
    "date": "2026-07-03"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/reports/2026-07-03"
    }
  }
}

3. Bấm nút **Test**.

**Kết quả dự kiến ở giai đoạn hiện tại:**
- `statusCode` = `404`
- `message` = `Chưa có báo cáo cho ngày này.`
*(Lưu ý: Đây là phản hồi phản ánh đúng trạng thái nghiệp vụ hiện tại của hệ thống).*

![Test Lambda trực tiếp](/images/5-Workshop/5.13-lambda-api-handler/5.13.6-test-lambda.png)