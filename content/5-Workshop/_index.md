---
title: "Workshop"
date : 2026-07-05
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Workshop

## Overview

This workshop demonstrates how to build a complete **Smart Home Energy Waste Monitoring & Alert System using Virtual Sensors on AWS** based on a fully Serverless architecture.

Throughout this workshop, participants will deploy a cloud-native solution capable of monitoring household energy consumption, detecting electricity waste automatically, and delivering real-time notifications to users.

The entire solution leverages AWS managed services, enabling high scalability, reduced operational costs, improved availability, and eliminating the need to manage servers.

Besides implementing the core application, this workshop also covers system monitoring, authentication, API development, report generation, frontend deployment, security best practices, and resource cleanup.

During this workshop, participants will work with the following AWS services:

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

After completing this workshop, participants will be able to:

- Understand how to build an end-to-end Serverless solution on AWS.
- Simulate IoT sensor data using AWS Lambda.
- Detect electricity waste automatically and generate real-time alerts.
- Develop secure REST APIs using Amazon Cognito and API Gateway.
- Generate automated reports and store them in Amazon S3.
- Deploy a frontend application using AWS Amplify.
- Deliver static content through Amazon CloudFront while protecting the application with AWS WAF.
- Remove all deployed AWS resources to minimize unnecessary cloud costs.

---

# Workshop Content

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Create AWS Budget](5.3-create-budget/)
4. [Create Amazon DynamoDB](5.4-dynamodb/)
5. [Create Amazon SNS](5.5-sns/)
6. [Deploy Lambda Waste Detector](5.6-lambda-waste-detector/)
7. [Deploy Lambda Virtual Sensor](5.7-lambda-virtual-sensor/)
8. [Configure AWS IoT Core](5.8-AWS-IoT-Core/)
9. [Configure EventBridge Scheduler](5.9-EventBridge-Scheduler/)
10. [Configure Amazon CloudWatch Logs](5.10-CloudWatch-Logs/)
11. [Configure Amazon Cognito](5.11-Amazon-Cognito/)
12. [Create HTTP API Gateway](5.12-api-gateway-http-api/)
13. [Deploy Lambda API Handler](5.13-lambda-api-handler/)
14. [Create Amazon S3 Report Bucket](5.14-s3-report-bucket/)
15. [Deploy Lambda Report Generator](5.15-lambda-report-generator/)
16. [Deploy Frontend Application](5.16-Deploy-Frontend-Application/)
17. [Configure Amazon CloudFront & AWS WAF](5.17-cloudfront-waf-custom/)
18. [Clean Up Resources](5.18-CleanUp/)