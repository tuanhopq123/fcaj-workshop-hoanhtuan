---
title : "Introduction"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

# Giới thiệu

## Smart Home Energy Waste Monitoring & Alert System

Trong bối cảnh các thiết bị điện thông minh ngày càng được sử dụng rộng rãi trong gia đình và doanh nghiệp, việc theo dõi mức tiêu thụ điện năng và phát hiện các hành vi sử dụng điện không hiệu quả trở thành một yêu cầu quan trọng. Việc để các thiết bị hoạt động khi không có người sử dụng không chỉ gây lãng phí điện năng mà còn làm tăng chi phí vận hành và ảnh hưởng đến mục tiêu tiết kiệm năng lượng.

**Smart Home Energy Waste Monitoring & Alert System** là một hệ thống giám sát tiêu thụ điện được xây dựng trên nền tảng AWS Cloud nhằm tự động phát hiện các trường hợp lãng phí điện và gửi cảnh báo đến người dùng theo thời gian thực.

Hệ thống sử dụng kiến trúc **Serverless**, giúp giảm chi phí vận hành, dễ dàng mở rộng và không cần quản lý máy chủ. Toàn bộ dữ liệu cảm biến được mô phỏng thông qua các **Virtual Sensors** được xây dựng bằng AWS Lambda.

Các cảm biến ảo mô phỏng các thông số như:

- Điện áp (Voltage)
- Dòng điện (Current)
- Công suất tiêu thụ (Power Consumption)
- Trạng thái thiết bị (Device Status)
- Trạng thái có người trong phòng (Occupancy Status)

Hệ thống xác định một trường hợp **lãng phí điện** khi đồng thời thỏa mãn các điều kiện sau:

- Thiết bị vẫn đang hoạt động.
- Không phát hiện người trong phòng.
- Công suất tiêu thụ vượt quá ngưỡng được cấu hình.

Sau khi phát hiện, hệ thống sẽ tự động:

- Lưu dữ liệu Telemetry vào Amazon DynamoDB.
- Lưu thông tin cảnh báo.
- Gửi Email cảnh báo thông qua Amazon SNS.
- Hỗ trợ tạo báo cáo định kỳ để phục vụ việc phân tích và thống kê.

---

# Mục tiêu của Workshop

Sau khi hoàn thành Workshop này, người học sẽ có thể:

- Hiểu cách xây dựng một hệ thống IoT Serverless trên AWS.
- Kết nối và xử lý dữ liệu cảm biến bằng AWS IoT Core.
- Xây dựng luồng xử lý dữ liệu bằng AWS Lambda.
- Lưu trữ dữ liệu trên Amazon DynamoDB.
- Gửi Email cảnh báo bằng Amazon SNS.
- Triển khai REST API với Amazon API Gateway.
- Xác thực người dùng bằng Amazon Cognito.
- Tạo báo cáo tự động và lưu trữ trên Amazon S3.
- Triển khai giao diện Web bằng AWS Amplify Hosting.
- Bảo vệ ứng dụng với AWS WAF.

---

# Tổng quan Workshop

Trong Workshop này, chúng ta sẽ triển khai hoàn chỉnh hệ thống **Smart Home Energy Waste Monitoring & Alert System** theo kiến trúc Serverless trên nền tảng AWS.

Kiến trúc của hệ thống được chia thành các luồng chức năng chính như sau:

### Virtual Sensor Flow

Amazon EventBridge sẽ kích hoạt **Lambda Virtual Sensor** theo chu kỳ mỗi phút để mô phỏng dữ liệu cảm biến.

Các dữ liệu sau khi được tạo sẽ được gửi đến **AWS IoT Core** thông qua giao thức MQTT.

---

### Waste Detection Flow

AWS IoT Rule sẽ tiếp nhận dữ liệu từ IoT Core và chuyển đến **Lambda Waste Detector**.

Lambda sẽ phân tích dữ liệu cảm biến để xác định các trường hợp lãng phí điện.

Nếu phát hiện bất thường, hệ thống sẽ:

- Lưu Telemetry vào Amazon DynamoDB.
- Lưu thông tin Alert.
- Gửi Email cảnh báo bằng Amazon SNS.

---

### Authentication & API Flow

Người dùng đăng nhập thông qua **Amazon Cognito**.

Sau khi xác thực thành công, các yêu cầu từ Web Application sẽ được gửi đến **Amazon API Gateway**.

API Gateway sẽ kích hoạt **Lambda API Handler** để truy xuất dữ liệu từ DynamoDB và trả kết quả về giao diện.

---

### Report Generation Flow

Lambda Report Generator sẽ đọc dữ liệu từ DynamoDB theo lịch trình.

Sau khi xử lý, báo cáo sẽ được xuất dưới định dạng JSON và lưu vào **Amazon S3** để phục vụ việc lưu trữ và tải xuống sau này.

---

### Frontend Deployment

Giao diện người dùng được phát triển bằng **Next.js** và triển khai trên **AWS Amplify Hosting**.

Để tăng cường bảo mật, toàn bộ lưu lượng truy cập HTTP/HTTPS sẽ được bảo vệ thông qua **AWS WAF**, giúp giảm thiểu các cuộc tấn công phổ biến vào ứng dụng Web.

---

# Kiến trúc tổng thể của hệ thống

Hình dưới đây mô tả toàn bộ kiến trúc triển khai của hệ thống Smart Home Energy Waste Monitoring & Alert System trên nền tảng AWS.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)