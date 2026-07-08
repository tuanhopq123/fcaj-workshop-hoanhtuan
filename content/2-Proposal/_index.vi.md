---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# SMART HOME ENERGY WASTE MONITORING & ALERT SYSTEM 
## Giải pháp AWS Serverless cho giám sát và cảnh báo lãng phí điện bằng cảm biến ảo 

### 1. Tóm tắt điều hành  
Smart Home Energy Waste Monitoring & Alert System là hệ thống giám sát tiêu thụ điện và phát hiện lãng phí điện theo thời gian thực, được xây dựng trên nền tảng AWS Serverless. Hệ thống sử dụng cảm biến ảo chạy bằng AWS Lambda để mô phỏng dữ liệu điện năng như công suất, điện áp, dòng điện, trạng thái thiết bị và trạng thái có người trong phòng. Dữ liệu được truyền qua AWS IoT Core, xử lý bằng Lambda Waste Detector, lưu trữ trong Amazon DynamoDB và gửi cảnh báo qua Amazon SNS khi phát hiện thiết bị đang bật nhưng không có người sử dụng.

Nền tảng được thiết kế phù hợp cho mô hình smart home, phòng lab hoặc phòng học thông minh, nơi cần theo dõi tình trạng tiêu thụ điện và giảm lãng phí năng lượng. Giao diện dashboard được xây dựng bằng React, Next.js và TailwindCSS, triển khai bằng AWS Amplify, bảo vệ bởi AWS WAF, phân phối qua Amazon CloudFront và xác thực người dùng bằng Amazon Cognito.  

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Trong các phòng lab, phòng học hoặc không gian làm việc chung, thiết bị điện như đèn, quạt, máy lạnh hoặc máy tính thường bị quên tắt sau khi không còn người sử dụng. Việc này gây lãng phí điện năng, tăng chi phí vận hành và làm giảm hiệu quả quản lý năng lượng. Ngoài ra, nếu chỉ kiểm tra thủ công, người quản lý khó có thể theo dõi liên tục trạng thái tiêu thụ điện theo thời gian thực.

Các hệ thống giám sát điện truyền thống thường cần cảm biến thật, máy chủ riêng, cơ sở dữ liệu cố định và chi phí triển khai cao. Đối với đồ án hoặc mô hình thử nghiệm, việc dùng cảm biến thật có thể làm tăng độ phức tạp và chi phí.  

*Giải pháp*  
Giải pháp đề xuất sử dụng kiến trúc AWS Serverless để xây dựng hệ thống giám sát điện bằng cảm biến ảo. AWS Lambda Virtual Sensor sẽ tự động sinh dữ liệu điện năng định kỳ mỗi 1 phút thông qua Amazon EventBridge. Dữ liệu này được gửi đến AWS IoT Core bằng giao thức MQTT, sau đó AWS IoT Rule chuyển dữ liệu sang Lambda Waste Detector để phân tích.

Khi phát hiện tình huống lãng phí điện, ví dụ thiết bị đang bật, không có người trong phòng và công suất vượt ngưỡng cho phép, hệ thống sẽ thực hiện song song hai hành động: lưu telemetry và alert vào Amazon DynamoDB, đồng thời gửi cảnh báo qua Amazon SNS đến email người dùng.

Ngoài ra, hệ thống có Lambda Report Generator chạy hằng ngày lúc 00:05 AM để đọc dữ liệu từ DynamoDB, tạo báo cáo và lưu vào Amazon S3 Report Bucket. Dashboard có thể gọi Amazon API Gateway và Lambda API Handler để xem dữ liệu giám sát, lịch sử cảnh báo và tải báo cáo.  

*Lợi ích  
Giải pháp giúp tự động hóa quá trình giám sát điện năng, giảm phụ thuộc vào kiểm tra thủ công và cung cấp cảnh báo gần thời gian thực khi có dấu hiệu lãng phí điện. Do sử dụng các dịch vụ serverless như AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon EventBridge, Amazon SNS và Amazon S3, hệ thống có khả năng mở rộng tốt, chi phí vận hành thấp và không cần quản lý máy chủ.

Đối với phạm vi đồ án, hệ thống có thể triển khai với chi phí thấp, phù hợp ngân sách thử nghiệm khoảng 30–50 USD hoặc thấp hơn nếu tối ưu số lần gọi dịch vụ. Đồng thời, kiến trúc có thể mở rộng trong tương lai để kết nối cảm biến thật, bổ sung nhiều phòng, nhiều thiết bị và dashboard phân tích nâng cao. 

### 3. Kiến trúc giải pháp  
Hệ thống được triển khai theo kiến trúc AWS Serverless tại region ap-southeast-1 Singapore. Lớp truy cập người dùng gồm Amazon Route 53, Amazon CloudFront, AWS WAF và AWS Amplify. Người dùng truy cập dashboard thông qua tên miền được quản lý bởi Route 53. CloudFront đóng vai trò CDN/edge delivery, AWS WAF bảo vệ lớp frontend, còn AWS Amplify host ứng dụng Next.js.

Lớp xác thực và API sử dụng Amazon Cognito, Amazon API Gateway và Lambda API Handler. Người dùng đăng nhập thông qua Cognito để nhận JWT token. Khi dashboard gọi API, API Gateway kiểm tra token và chuyển request đến Lambda API Handler. Lambda API Handler đọc/ghi dữ liệu từ Amazon DynamoDB và truy xuất báo cáo từ Amazon S3 Report Bucket.

Lớp xử lý dữ liệu cảm biến sử dụng Amazon EventBridge, Lambda Virtual Sensor, AWS IoT Core, IoT Rule và Lambda Waste Detector. EventBridge kích hoạt Lambda Virtual Sensor mỗi 1 phút để sinh dữ liệu điện năng giả lập. Dữ liệu được publish lên AWS IoT Core, sau đó IoT Rule định tuyến dữ liệu đến Lambda Waste Detector. Lambda Waste Detector phân tích điều kiện lãng phí điện và thực hiện hai nhánh song song: lưu dữ liệu vào DynamoDB và gửi cảnh báo qua SNS Email.

Lớp báo cáo sử dụng EventBridge rule chạy hằng ngày lúc 00:05 AM để kích hoạt Lambda Report Generator. Lambda này đọc dữ liệu telemetry và alerts từ DynamoDB, tổng hợp báo cáo theo ngày và ghi file báo cáo vào Amazon S3 Report Bucket.

Amazon CloudWatch được sử dụng để thu thập logs, metrics và hỗ trợ monitoring cho các thành phần như Lambda, API Gateway, EventBridge, IoT Core và SNS. Nhờ đó, nhóm có thể kiểm tra hệ thống có chạy đúng lịch không, Lambda có lỗi không, IoT Rule có gọi Waste Detector không và SNS có gửi cảnh báo thành công không.  


*Dịch vụ AWS sử dụng*  
- Amazon Route 53: Quản lý tên miền và điều hướng người dùng đến lớp phân phối nội dung.  
- Amazon CloudFront: Phân phối frontend qua CDN, giúp dashboard truy cập nhanh hơn và ổn định hơn.  
- AWS WAF: Bảo vệ lớp frontend khỏi các request bất thường hoặc độc hại. 
- AWS Amplify: Lưu trữ và triển khai ứng dụng web Next.js cho dashboard.  
- Amazon Cognito: Quản lý đăng nhập, xác thực người dùng và cấp JWT token.
- Amazon API Gateway: Cung cấp API endpoint để frontend gọi đến backend.  
- AWS Lambda: Xử lý backend serverless, gồm 4 hàm chính: Lambda API Handler, Lambda Virtual Sensor, Lambda Waste Detector và Lambda Report Generator.
- Amazon EventBridge: Tạo lịch chạy tự động cho cảm biến ảo mỗi 1 phút và tạo báo cáo hằng ngày lúc 00:05 AM.
- AWS IoT Core: Tiếp nhận dữ liệu điện năng giả lập thông qua giao thức MQTT.
- AWS IoT Core Rule: Định tuyến dữ liệu telemetry từ IoT Core đến Lambda Waste Detector.
- Amazon DynamoDB: Lưu dữ liệu dùng chung gồm Rooms, Telemetry, Alerts và Reports Metadata.
- Amazon SNS: Gửi cảnh báo qua email khi phát hiện lãng phí điện.
- Amazon S3: Lưu trữ file báo cáo hằng ngày trong Report Bucket.
- Amazon CloudWatch: Theo dõi logs, metrics và hỗ trợ debug cho Lambda, API Gateway, EventBridge, IoT Core và SNS.
- AWS Budgets: Theo dõi chi phí và gửi cảnh báo khi ngân sách vượt ngưỡng dự kiến.

*Thiết kế thành phần*  
- Người dùng: Truy cập dashboard thông qua trình duyệt web để xem dữ liệu điện năng, cảnh báo và báo cáo.
- Giao diện web: Dashboard được xây dựng bằng React, Next.js và TailwindCSS, triển khai trên AWS Amplify.
- Lớp Edge/Frontend: Amazon Route 53 điều hướng domain đến Amazon CloudFront. AWS WAF bảo vệ CloudFront, sau đó CloudFront phân phối ứng dụng frontend từ AWS Amplify.
- Quản lý người dùng: Amazon Cognito thực hiện đăng nhập, xác thực người dùng và cấp JWT token.
- Backend API: Amazon API Gateway nhận request từ dashboard, kiểm tra JWT token và gọi Lambda API Handler để xử lý nghiệp vụ.
- Cảm biến ảo: Lambda Virtual Sensor được kích hoạt mỗi 1 phút bởi Amazon EventBridge để sinh dữ liệu điện năng giả lập như công suất, điện áp, dòng điện, trạng thái thiết bị và trạng thái có người trong phòng.
- Tiếp nhận dữ liệu IoT: AWS IoT Core nhận dữ liệu MQTT từ Lambda Virtual Sensor. AWS IoT Core Rule định tuyến dữ liệu này đến Lambda Waste Detector.
- Phát hiện lãng phí điện: Lambda Waste Detector kiểm tra điều kiện lãng phí điện, ví dụ thiết bị đang bật, không có người trong phòng và công suất vượt ngưỡng cho phép.
- Lưu trữ dữ liệu: Amazon DynamoDB lưu telemetry, alerts, rooms và reports metadata trong một bảng dữ liệu dùng chung.
- Cảnh báo: Amazon SNS gửi email cảnh báo khi phát hiện tình trạng lãng phí điện.
- Báo cáo: Lambda Report Generator chạy hằng ngày lúc 00:05 AM, đọc dữ liệu từ DynamoDB, tổng hợp báo cáo và lưu vào Amazon S3 Report Bucket.
- Giám sát hệ thống: Amazon CloudWatch ghi logs và metrics để kiểm tra Lambda có chạy đúng lịch không, IoT Rule có gọi detector không, API có lỗi không và SNS có gửi cảnh báo thành công không.  

### 4. Lộ trình va Mốc triển khai 
- Giai đoạn 1 — Thiết kế và chuẩn bị:
Hoàn thiện yêu cầu hệ thống, thiết kế sơ đồ kiến trúc AWS, xác định các service cần dùng và thiết lập AWS Budget để kiểm soát chi phí.
- Giai đoạn 2 — Triển khai luồng cảm biến ảo:
Tạo DynamoDB, SNS, Lambda Virtual Sensor, Lambda Waste Detector, IoT Core, IoT Core Rule và EventBridge rule chạy mỗi 1 phút. Kiểm tra dữ liệu có được sinh, truyền qua IoT Core, xử lý và lưu vào DynamoDB hay không.
- Giai đoạn 3 — Triển khai API và xác thực:
Tạo Cognito User Pool, API Gateway và Lambda API Handler. Kiểm tra frontend hoặc Postman có thể gọi API bằng JWT token và đọc dữ liệu từ DynamoDB hay không.
- Giai đoạn 4 — Triển khai dashboard và báo cáo:
Deploy dashboard Next.js lên AWS Amplify. Tạo Lambda Report Generator, EventBridge rule chạy hằng ngày lúc 00:05 AM và S3 Report Bucket để lưu file báo cáo.
- Giai đoạn 5 — Kiểm thử và hoàn thiện:
Kiểm tra toàn bộ hệ thống, xem logs trên CloudWatch, test email cảnh báo qua SNS, kiểm tra report trong S3 và tối ưu chi phí trước khi trình bày đồ án.  

 

### 5. Ước tính ngân sách  
Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)  
Hoặc tải [tệp ước tính ngân sách](../attachments/budget_estimation.pdf).  

*Chi phí hạ tầng*  
- AWS Lambda: 0,00 USD/tháng (1.000 request, 512 MB lưu trữ).  
- S3 Standard: 0,15 USD/tháng (6 GB, 2.100 request, 1 GB quét).  
- Truyền dữ liệu: 0,02 USD/tháng (1 GB vào, 1 GB ra).  
- AWS Amplify: 0,35 USD/tháng (256 MB, request 500 ms).  
- Amazon API Gateway: 0,01 USD/tháng (2.000 request).  
- AWS Glue ETL Jobs: 0,02 USD/tháng (2 DPU).  
- AWS Glue Crawlers: 0,07 USD/tháng (1 crawler).  
- MQTT (IoT Core): 0,08 USD/tháng (5 thiết bị, 45.000 tin nhắn).  

*Tổng*: 0,7 USD/tháng, 8,40 USD/12 tháng  
- *Phần cứng*: 265 USD một lần (Raspberry Pi 5 và cảm biến).  

### 6. Đánh giá rủi ro  
*Ma trận rủi ro*  
- Vượt ngân sách AWS: Ảnh hưởng trung bình, xác suất trung bình. Nguyên nhân có thể do CloudWatch logs tăng, WAF/CloudFront phát sinh chi phí hoặc EventBridge chạy liên tục.
- Lambda thiếu quyền IAM: Ảnh hưởng cao, xác suất trung bình. Có thể làm Lambda không ghi được DynamoDB, không publish SNS hoặc không gửi dữ liệu đến IoT Core.
- SNS không gửi được email: Ảnh hưởng trung bình, xác suất trung bình. Nguyên nhân thường gặp là email subscription chưa được xác nhận.
- IoT Rule không gọi Lambda Waste Detector: Ảnh hưởng cao, xác suất trung bình. Có thể do sai topic MQTT, sai SQL statement hoặc thiếu permission invoke Lambda.
- API Gateway bị lỗi xác thực JWT: Ảnh hưởng cao, xác suất trung bình. Có thể do cấu hình Cognito authorizer sai hoặc frontend gửi thiếu Authorization header.
- Dữ liệu cảm biến ảo chưa sát thực tế: Ảnh hưởng trung bình, xác suất cao. Do dữ liệu được mô phỏng nên cần thiết kế rule phát hiện phù hợp để demo rõ ràng.
- Dashboard không đọc được API: Ảnh hưởng trung bình, xác suất trung bình. Nguyên nhân có thể do CORS, sai endpoint API Gateway hoặc sai token.
- Báo cáo không được tạo đúng lịch: Ảnh hưởng trung bình, xác suất thấp. Có thể do EventBridge rule sai giờ, Lambda timeout hoặc thiếu quyền ghi S3. 

*Chiến lược giảm thiểu*  
- Chi phí: Tạo AWS Budget, theo dõi Billing Dashboard và kiểm soát CloudWatch Logs retention.
- IAM Permission: Tạo quyền tối thiểu cần thiết cho từng Lambda, kiểm tra kỹ quyền DynamoDB, SNS, IoT Core và S3.
- SNS Email: Xác nhận email subscription ngay sau khi tạo SNS topic.
- IoT Rule: Test thủ công Lambda Virtual Sensor, kiểm tra topic MQTT và xem logs của Lambda Waste Detector trong CloudWatch.
- JWT/Cognito: Test đăng nhập, lấy JWT token và gọi API Gateway bằng Postman hoặc dashboard.
- CORS: Cấu hình CORS cho API Gateway để frontend Amplify gọi được backend.
- Report: Test Lambda Report Generator thủ công trước, sau đó mới gắn EventBridge rule Daily 00:05 AM.
- Dữ liệu mô phỏng: Tạo nhiều kịch bản cảm biến ảo như có người/không có người, thiết bị bật/tắt và công suất cao/thấp để chứng minh chức năng phát hiện lãng phí điện.  

*Kế hoạch dự phòng*  
- Nếu AWS IoT Core gặp lỗi cấu hình, có thể test tạm bằng cách gọi trực tiếp Lambda Waste Detector với JSON sample.
- Nếu Cognito chưa hoàn thiện, có thể demo API Gateway ở chế độ test trước, sau đó bổ sung JWT authorizer.
- Nếu Amplify chưa deploy kịp, có thể chạy frontend local và gọi API Gateway thật để chứng minh backend AWS hoạt động.
- Nếu report chưa tạo tự động, có thể chạy Lambda Report Generator thủ công để sinh file báo cáo trong S3.
- Nếu chi phí tăng bất thường, tạm disable EventBridge rule và xóa log group không cần thiết sau khi đã chụp minh chứng.  

### 7. Kết quả kỳ vọng  
- Cải tiến kỹ thuật:
Hệ thống giúp tự động hóa quá trình giám sát điện năng trong smart home hoặc phòng lab, thay thế việc kiểm tra thủ công bằng một pipeline serverless chạy định kỳ. Dữ liệu điện năng được sinh bởi cảm biến ảo, truyền qua AWS IoT Core, phân tích bằng Lambda và lưu trữ tập trung trong DynamoDB. Khi phát hiện lãng phí điện, hệ thống có thể gửi cảnh báo qua email gần thời gian thực.
- Giá trị vận hành:
Dashboard giúp người dùng theo dõi dữ liệu tiêu thụ điện, xem lịch sử cảnh báo và tải báo cáo hằng ngày. Việc sử dụng AWS Serverless giúp giảm nhu cầu quản lý máy chủ, đơn giản hóa triển khai và dễ mở rộng khi cần thêm phòng, thêm thiết bị hoặc kết nối cảm biến thật trong tương lai.
- Khả năng mở rộng:
Trong tương lai, hệ thống có thể mở rộng từ cảm biến ảo sang cảm biến thật như smart meter, ESP32 hoặc thiết bị IoT đo công suất. Ngoài ra, có thể bổ sung phân tích xu hướng tiêu thụ điện, dự đoán bất thường, tối ưu lịch bật/tắt thiết bị và tích hợp dashboard quản trị nhiều phòng hoặc nhiều tòa nhà.
![Kiến trúc](/images/2-Proposal/2.architecture.png)