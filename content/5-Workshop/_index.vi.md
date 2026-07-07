---
title: "Workshop"
date : 2026-07-05
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Workshop

## Giới thiệu

Workshop này hướng dẫn triển khai hoàn chỉnh hệ thống **Smart Home Energy Waste Monitoring & Alert System using Virtual Sensors on AWS** theo kiến trúc **AWS Serverless**.

Thông qua Workshop, người học sẽ từng bước xây dựng một hệ thống giám sát mức tiêu thụ điện năng trong nhà thông minh bằng cảm biến ảo, tự động phát hiện các trường hợp lãng phí điện và gửi cảnh báo đến người dùng theo thời gian thực.

Toàn bộ hệ thống được xây dựng dựa trên các dịch vụ Cloud Native của AWS, giúp tăng khả năng mở rộng, giảm chi phí vận hành và không cần quản lý máy chủ. Ngoài việc triển khai các thành phần cốt lõi, Workshop còn hướng dẫn cấu hình bảo mật, giám sát hệ thống, triển khai giao diện người dùng và dọn dẹp tài nguyên sau khi hoàn thành.

Trong quá trình thực hiện, người học sẽ được làm việc với nhiều dịch vụ AWS như:

- Amazon DynamoDB
- AWS Lambda
- Amazon SNS
- AWS IoT Core
- Amazon EventBridge Scheduler
- Amazon Cognito
- Amazon API Gateway
- Amazon S3
- Amazon CloudWatch
- Amazon CloudFront
- AWS WAF
- AWS Amplify

Sau khi hoàn thành Workshop, người học sẽ có thể:

- Hiểu quy trình xây dựng một hệ thống Serverless hoàn chỉnh trên AWS.
- Xây dựng luồng thu thập dữ liệu từ cảm biến ảo đến hệ thống xử lý.
- Phát hiện và cảnh báo các trường hợp lãng phí điện theo thời gian thực.
- Xây dựng REST API bảo mật bằng Amazon Cognito và API Gateway.
- Sinh báo cáo tự động và lưu trữ trên Amazon S3.
- Triển khai ứng dụng Web lên AWS Amplify.
- Phân phối nội dung bằng Amazon CloudFront và bảo vệ hệ thống với AWS WAF.
- Thực hiện dọn dẹp toàn bộ tài nguyên nhằm tối ưu chi phí sau khi hoàn thành Workshop.

---

# Nội dung Workshop

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Prerequisite](5.2-Prerequiste/)
3. [Create AWS Budget](5.3-create-budget/)
4. [Create Amazon DynamoDB](5.4-dynamodb/)
5. [Create Amazon SNS](5.5-sns/)
6. [Deploy Lambda Waste Detector](5.6-lambda-waste-detector/)
7. [Deploy Lambda Virtual Sensor](5.7-lambda-virtual-sensor/)
8. [Configure AWS IoT Core](5.8-AWS-IoT-Core/)
9. [Configure EventBridge Scheduler](5.9-EventBridge-Scheduler/)
10. [Configure CloudWatch Logs](5.10-CloudWatch-Logs/)
11. [Configure Amazon Cognito](5.11-Amazon-Cognito/)
12. [Create HTTP API Gateway](5.12-api-gateway-http-api/)
13. [Deploy Lambda API Handler](5.13-lambda-api-handler/)
14. [Create Amazon S3 Report Bucket](5.14-s3-report-bucket/)
15. [Deploy Lambda Report Generator](5.15-lambda-report-generator/)
16. [Deploy Frontend Application](5.16-Deploy-Frontend-Application/)
17. [Configure CloudFront & AWS WAF](5.17-cloudfront-waf-custom/)
18. [Clean Up Resources](5.18-CleanUp/)