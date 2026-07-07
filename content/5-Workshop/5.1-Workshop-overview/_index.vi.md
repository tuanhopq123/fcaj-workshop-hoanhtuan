---
title : "Giới thiệu"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

# Giới thiệu

## Hệ thống Smart Home Energy Waste Monitoring & Alert System

Trong bối cảnh các thiết bị điện thông minh ngày càng được sử dụng rộng rãi trong gia đình và doanh nghiệp, việc giám sát mức tiêu thụ điện năng và phát hiện các hành vi sử dụng điện không hiệu quả trở thành một yêu cầu quan trọng. Việc để các thiết bị hoạt động khi không có người sử dụng không chỉ gây lãng phí điện năng mà còn làm tăng chi phí vận hành, giảm hiệu quả sử dụng tài nguyên và ảnh hưởng đến mục tiêu tiết kiệm năng lượng.

**Smart Home Energy Waste Monitoring & Alert System** là một hệ thống được xây dựng trên nền tảng Amazon Web Services (AWS) nhằm giám sát dữ liệu tiêu thụ điện theo thời gian thực, tự động phát hiện các trường hợp lãng phí điện và gửi cảnh báo đến người dùng.

Hệ thống được triển khai theo kiến trúc **Serverless**, tận dụng các dịch vụ được quản lý hoàn toàn của AWS để giảm chi phí vận hành, tăng khả năng mở rộng và không cần quản lý máy chủ.

Để mô phỏng dữ liệu thực tế, hệ thống sử dụng **Virtual Sensors** được xây dựng bằng **AWS Lambda**. Các cảm biến ảo sẽ tạo dữ liệu định kỳ bao gồm:

- Điện áp (Voltage)
- Dòng điện (Current)
- Công suất tiêu thụ (Power Consumption)
- Trạng thái thiết bị (Device Status)
- Trạng thái có người trong phòng (Occupancy Status)

Hệ thống xác định một trường hợp **lãng phí điện** khi đồng thời thỏa mãn các điều kiện sau:

- Thiết bị vẫn đang hoạt động.
- Không phát hiện người trong phòng.
- Công suất tiêu thụ vượt quá ngưỡng đã được cấu hình.

Khi phát hiện lãng phí điện, hệ thống sẽ tự động:

- Ghi dữ liệu Telemetry vào Amazon DynamoDB.
- Lưu thông tin cảnh báo.
- Gửi Email cảnh báo thông qua Amazon SNS.
- Hỗ trợ tạo báo cáo định kỳ phục vụ việc thống kê và phân tích dữ liệu.

---

# Mục tiêu của Workshop

Sau khi hoàn thành Workshop này, người học sẽ có thể:

- Hiểu quy trình xây dựng một hệ thống IoT theo kiến trúc Serverless trên AWS.
- Triển khai và xử lý dữ liệu cảm biến thông qua AWS IoT Core.
- Xây dựng các chức năng xử lý nghiệp vụ bằng AWS Lambda.
- Lưu trữ dữ liệu bằng Amazon DynamoDB.
- Gửi Email cảnh báo bằng Amazon SNS.
- Xây dựng RESTful API với Amazon API Gateway.
- Xác thực người dùng bằng Amazon Cognito.
- Tạo báo cáo tự động và lưu trữ trên Amazon S3.
- Triển khai giao diện Web bằng AWS Amplify Hosting.
- Bảo vệ ứng dụng bằng AWS WAF.

---

# Tổng quan Workshop

Trong Workshop này, chúng ta sẽ từng bước xây dựng hoàn chỉnh hệ thống **Smart Home Energy Waste Monitoring & Alert System** theo kiến trúc Serverless trên nền tảng AWS.

Kiến trúc của hệ thống được chia thành các luồng chức năng chính như sau:

### Luồng mô phỏng cảm biến (Virtual Sensor Flow)

Amazon EventBridge sẽ kích hoạt **Lambda Virtual Sensor** theo chu kỳ mỗi phút để tạo dữ liệu cảm biến mô phỏng.

Sau khi được tạo, dữ liệu sẽ được gửi đến **AWS IoT Core** thông qua giao thức MQTT để phục vụ quá trình xử lý tiếp theo.

---

### Luồng phát hiện lãng phí điện (Waste Detection Flow)

AWS IoT Rule sẽ tiếp nhận dữ liệu từ AWS IoT Core và chuyển đến **Lambda Waste Detector**.

Lambda sẽ phân tích dữ liệu cảm biến nhằm xác định các trường hợp sử dụng điện không hiệu quả.

Nếu phát hiện lãng phí điện, hệ thống sẽ:

- Lưu dữ liệu Telemetry vào Amazon DynamoDB.
- Lưu thông tin cảnh báo.
- Gửi Email cảnh báo đến người dùng thông qua Amazon SNS.

---

### Luồng xác thực và API (Authentication & API Flow)

Người dùng đăng nhập vào hệ thống thông qua **Amazon Cognito**.

Sau khi xác thực thành công, các yêu cầu từ giao diện Web sẽ được gửi đến **Amazon API Gateway**.

API Gateway sẽ kích hoạt **Lambda API Handler** để truy xuất dữ liệu từ DynamoDB và trả kết quả về giao diện người dùng.

---

### Luồng tạo báo cáo (Report Generation Flow)

Lambda Report Generator sẽ được kích hoạt theo lịch để đọc dữ liệu từ DynamoDB.

Sau khi xử lý, báo cáo sẽ được tạo dưới định dạng JSON và lưu trữ trong **Amazon S3**, phục vụ việc tải xuống và lưu trữ lâu dài.

---

### Giao diện người dùng (Frontend)

Giao diện Web được phát triển bằng **Next.js** và triển khai trên **AWS Amplify Hosting**.

Toàn bộ lưu lượng truy cập HTTP/HTTPS được bảo vệ bởi **AWS WAF**, góp phần giảm thiểu các cuộc tấn công phổ biến vào ứng dụng Web và nâng cao tính bảo mật cho hệ thống.

---

# Kiến trúc tổng thể của hệ thống

Hình dưới đây mô tả kiến trúc tổng thể của hệ thống **Smart Home Energy Waste Monitoring & Alert System** được triển khai trên nền tảng Amazon Web Services (AWS).

Thông qua sơ đồ này, người học có thể dễ dàng hình dung luồng xử lý dữ liệu từ quá trình mô phỏng cảm biến, thu thập dữ liệu, phân tích, phát hiện lãng phí điện, lưu trữ, gửi cảnh báo cho đến việc tạo báo cáo và hiển thị dữ liệu trên giao diện Web.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)