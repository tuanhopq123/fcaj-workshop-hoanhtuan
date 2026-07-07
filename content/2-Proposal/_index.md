---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


# SMART HOME ENERGY WASTE MONITORING & ALERT SYSTEM

## An AWS Serverless Solution for Monitoring and Alerting Energy Waste Using Virtual Sensors

### 1. Executive Summary

Smart Home Energy Waste Monitoring & Alert System is a real-time electricity consumption monitoring and energy waste detection system built on an AWS Serverless architecture. The system uses virtual sensors running on AWS Lambda to simulate energy data such as power, voltage, current, device status, and room occupancy status. The data is transmitted through AWS IoT Core, processed by Lambda Waste Detector, stored in Amazon DynamoDB, and alerts are sent through Amazon SNS when the system detects that a device is still turned on while no one is using the room.

The platform is suitable for smart homes, laboratories, classrooms, or shared working spaces where electricity consumption needs to be monitored and energy waste should be reduced. The dashboard interface is built with React, Next.js, and TailwindCSS, deployed using AWS Amplify, protected by AWS WAF, distributed through Amazon CloudFront, and secured with Amazon Cognito authentication.

### 2. Problem Statement

*Current Problem*

In laboratories, classrooms, or shared working spaces, electrical devices such as lights, fans, air conditioners, or computers are often left on after people have left the room. This causes energy waste, increases operating costs, and reduces the efficiency of energy management. In addition, if monitoring is performed manually, it is difficult for administrators to continuously track electricity consumption in real time.

Traditional electricity monitoring systems often require physical sensors, dedicated servers, fixed databases, and high deployment costs. For a student project or prototype, using physical sensors may increase both complexity and cost.

*Proposed Solution*

The proposed solution uses an AWS Serverless architecture to build an electricity monitoring system with virtual sensors. AWS Lambda Virtual Sensor automatically generates energy data every 1 minute through Amazon EventBridge. This data is sent to AWS IoT Core using the MQTT protocol, and then an AWS IoT Rule forwards the data to Lambda Waste Detector for analysis.

When the system detects an energy waste condition, such as a device being turned on while no one is in the room and the power consumption exceeds the defined threshold, it performs two actions in parallel: storing telemetry and alert data in Amazon DynamoDB and sending an email alert to the user through Amazon SNS.

In addition, the system includes a Lambda Report Generator that runs daily at 00:05 AM to read data from DynamoDB, generate a report, and store it in an Amazon S3 Report Bucket. The dashboard can call Amazon API Gateway and Lambda API Handler to view monitoring data, alert history, and download reports.

*Benefits*

The solution automates the electricity monitoring process, reduces dependence on manual checking, and provides near real-time alerts when signs of energy waste are detected. By using serverless services such as AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon EventBridge, Amazon SNS, and Amazon S3, the system is scalable, cost-efficient, and does not require server management.

Within the scope of the project, the system can be deployed at a low cost, suitable for a testing budget of around 30–50 USD or lower if service calls are optimized. The architecture can also be expanded in the future to connect real sensors, support more rooms and devices, and provide more advanced analytics dashboards.

### 3. Solution Architecture

The system is deployed using an AWS Serverless architecture in the ap-southeast-1 Singapore Region. The user access layer includes Amazon Route 53, Amazon CloudFront, AWS WAF, and AWS Amplify. Users access the dashboard through a domain managed by Route 53. CloudFront acts as the CDN/edge delivery layer, AWS WAF protects the frontend layer, and AWS Amplify hosts the Next.js application.

The authentication and API layer uses Amazon Cognito, Amazon API Gateway, and Lambda API Handler. Users sign in through Cognito to receive a JWT token. When the dashboard calls the API, API Gateway validates the token and forwards the request to Lambda API Handler. Lambda API Handler reads and writes data to Amazon DynamoDB and retrieves reports from the Amazon S3 Report Bucket.

The sensor data processing layer uses Amazon EventBridge, Lambda Virtual Sensor, AWS IoT Core, IoT Rule, and Lambda Waste Detector. EventBridge triggers Lambda Virtual Sensor every 1 minute to generate simulated electricity data. The data is published to AWS IoT Core, and then IoT Rule routes the data to Lambda Waste Detector. Lambda Waste Detector analyzes energy waste conditions and performs two parallel actions: storing data in DynamoDB and sending alerts through SNS Email.

The reporting layer uses an EventBridge rule that runs daily at 00:05 AM to trigger Lambda Report Generator. This Lambda function reads telemetry and alert data from DynamoDB, summarizes daily reports, and writes report files to the Amazon S3 Report Bucket.

Amazon CloudWatch is used to collect logs, metrics, and monitoring data for components such as Lambda, API Gateway, EventBridge, IoT Core, and SNS. This allows the team to verify whether the system runs on schedule, whether Lambda functions encounter errors, whether IoT Rule invokes Waste Detector, and whether SNS sends alerts successfully.

![Energy Waste Monitoring Architecture](/images/2-Proposal/ANH.jpg)

*AWS Services Used*

- Amazon Route 53: Manages the domain name and routes users to the content delivery layer.
- Amazon CloudFront: Distributes the frontend through a CDN, allowing the dashboard to load faster and more reliably.
- AWS WAF: Protects the frontend layer from abnormal or malicious requests.
- AWS Amplify: Hosts and deploys the Next.js web application for the dashboard.
- Amazon Cognito: Manages user sign-in, authentication, and JWT token issuance.
- Amazon API Gateway: Provides API endpoints for the frontend to call the backend.
- AWS Lambda: Handles serverless backend processing through four main functions: Lambda API Handler, Lambda Virtual Sensor, Lambda Waste Detector, and Lambda Report Generator.
- Amazon EventBridge: Creates scheduled triggers for the virtual sensor every 1 minute and for the daily report at 00:05 AM.
- AWS IoT Core: Receives simulated electricity data through the MQTT protocol.
- AWS IoT Core Rule: Routes telemetry data from IoT Core to Lambda Waste Detector.
- Amazon DynamoDB: Stores shared data, including Rooms, Telemetry, Alerts, and Reports Metadata.
- Amazon SNS: Sends email alerts when electricity waste is detected.
- Amazon S3: Stores daily report files in the Report Bucket.
- Amazon CloudWatch: Monitors logs and metrics and supports debugging for Lambda, API Gateway, EventBridge, IoT Core, and SNS.
- AWS Budgets: Tracks costs and sends alerts when the budget exceeds the expected threshold.

*Component Design*

- Users: Access the dashboard through a web browser to view electricity data, alerts, and reports.
- Web Interface: The dashboard is built with React, Next.js, and TailwindCSS, and deployed on AWS Amplify.
- Edge/Frontend Layer: Amazon Route 53 routes the domain to Amazon CloudFront. AWS WAF protects CloudFront, and CloudFront distributes the frontend application hosted on AWS Amplify.
- User Management: Amazon Cognito handles user sign-in, authentication, and JWT token issuance.
- Backend API: Amazon API Gateway receives requests from the dashboard, validates JWT tokens, and invokes Lambda API Handler to process business logic.
- Virtual Sensor: Lambda Virtual Sensor is triggered every 1 minute by Amazon EventBridge to generate simulated electricity data such as power, voltage, current, device status, and room occupancy status.
- IoT Data Ingestion: AWS IoT Core receives MQTT data from Lambda Virtual Sensor. AWS IoT Core Rule routes this data to Lambda Waste Detector.
- Energy Waste Detection: Lambda Waste Detector checks energy waste conditions, such as a device being turned on, no one being in the room, and power consumption exceeding the allowed threshold.
- Data Storage: Amazon DynamoDB stores telemetry, alerts, rooms, and reports metadata in a shared data table.
- Alerting: Amazon SNS sends email alerts when energy waste is detected.
- Reporting: Lambda Report Generator runs daily at 00:05 AM, reads data from DynamoDB, summarizes reports, and stores them in the Amazon S3 Report Bucket.
- System Monitoring: Amazon CloudWatch records logs and metrics to verify whether Lambda functions run on schedule, whether IoT Rule invokes the detector, whether APIs encounter errors, and whether SNS sends alerts successfully.

### 4. Roadmap and Deployment Milestones

- Phase 1 — Design and Preparation:  
Complete system requirements, design the AWS architecture diagram, identify required services, and set up AWS Budget to control costs.

- Phase 2 — Deploy the Virtual Sensor Flow:  
Create DynamoDB, SNS, Lambda Virtual Sensor, Lambda Waste Detector, IoT Core, IoT Core Rule, and an EventBridge rule that runs every 1 minute. Verify whether data is generated, transmitted through IoT Core, processed, and stored in DynamoDB.

- Phase 3 — Deploy API and Authentication:  
Create a Cognito User Pool, API Gateway, and Lambda API Handler. Test whether the frontend or Postman can call the API using a JWT token and read data from DynamoDB.

- Phase 4 — Deploy Dashboard and Reporting:  
Deploy the Next.js dashboard to AWS Amplify. Create Lambda Report Generator, an EventBridge rule that runs daily at 00:05 AM, and an S3 Report Bucket to store report files.

- Phase 5 — Testing and Finalization:  
Test the entire system, review logs in CloudWatch, test SNS email alerts, verify reports in S3, and optimize costs before the final project presentation.

### 5. Budget Estimation

Costs can be estimated using [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01).  
Or download the [budget estimation file](../attachments/budget_estimation.pdf).

*Infrastructure Costs*

- AWS Lambda: 0.00 USD/month for low-volume demo usage.
- Amazon DynamoDB: 0.00–0.10 USD/month for small on-demand data storage.
- AWS IoT Core: 0.05–0.10 USD/month for MQTT messages and IoT rule processing.
- Amazon SNS: 0.00–0.05 USD/month for a small number of email alerts.
- Amazon API Gateway: approximately 0.01 USD/month for around 2,000 API requests.
- Amazon S3 Report Bucket: 0.00–0.05 USD/month for storing daily report files.
- AWS Amplify: approximately 0.30–1.00 USD/month for frontend build, deployment, and hosting.
- Amazon CloudFront: approximately 0.00–0.10 USD/month for low demo traffic.
- AWS WAF: approximately 6.00–8.00 USD/month if enabled with one Web ACL and several basic rules.
- Amazon CloudWatch: approximately 0.00–0.50 USD/month depending on log volume.

*Estimated Total*

- Core AWS demo without WAF and Route 53: approximately 0.5–2 USD/month.
- Full architecture with WAF, Route 53, CloudFront, and Amplify: approximately 7–10 USD/month.
- Recommended project budget: 30–50 USD for the full testing and demonstration period.

### 6. Risk Assessment

*Risk Matrix*

- AWS budget overrun: Medium impact, medium probability. This may be caused by increased CloudWatch logs, WAF/CloudFront costs, or EventBridge running continuously.
- Missing IAM permissions for Lambda: High impact, medium probability. This may prevent Lambda from writing to DynamoDB, publishing to SNS, or sending data to IoT Core.
- SNS email not sent: Medium impact, medium probability. A common cause is that the email subscription has not been confirmed.
- IoT Rule does not invoke Lambda Waste Detector: High impact, medium probability. This may be caused by an incorrect MQTT topic, incorrect SQL statement, or missing Lambda invoke permission.
- API Gateway JWT authentication error: High impact, medium probability. This may be caused by incorrect Cognito authorizer configuration or a missing Authorization header from the frontend.
- Simulated sensor data is not realistic enough: Medium impact, high probability. Since the data is simulated, the detection rules must be designed carefully for a clear demonstration.
- Dashboard cannot read the API: Medium impact, medium probability. This may be caused by CORS issues, an incorrect API Gateway endpoint, or an invalid token.
- Report is not generated on schedule: Medium impact, low probability. This may be caused by an incorrect EventBridge schedule, Lambda timeout, or missing S3 write permission.

*Mitigation Strategies*

- Cost: Create AWS Budget, monitor the Billing Dashboard, and control CloudWatch Logs retention.
- IAM Permission: Apply least-privilege permissions for each Lambda function and verify DynamoDB, SNS, IoT Core, and S3 permissions carefully.
- SNS Email: Confirm the email subscription immediately after creating the SNS topic.
- IoT Rule: Manually test Lambda Virtual Sensor, verify the MQTT topic, and check Lambda Waste Detector logs in CloudWatch.
- JWT/Cognito: Test sign-in, obtain a JWT token, and call API Gateway using Postman or the dashboard.
- CORS: Configure CORS for API Gateway so that the Amplify frontend can call the backend.
- Report: Test Lambda Report Generator manually before attaching the Daily 00:05 AM EventBridge rule.
- Simulated Data: Create multiple virtual sensor scenarios, such as occupied/unoccupied room, device on/off, and high/low power usage to clearly demonstrate energy waste detection.

*Contingency Plan*

- If AWS IoT Core configuration fails, Lambda Waste Detector can be tested directly using a sample JSON event.
- If Cognito is not completed in time, API Gateway can be demonstrated in test mode first, then the JWT authorizer can be added later.
- If Amplify deployment is not ready, the frontend can be run locally and call the real API Gateway endpoint to prove that the AWS backend works.
- If automatic report generation is not ready, Lambda Report Generator can be run manually to generate a report file in S3.
- If costs increase unexpectedly, the EventBridge rule can be disabled temporarily and unnecessary log groups can be deleted after screenshots are captured as evidence.

### 7. Expected Outcomes

- Technical Improvement:  
The system automates electricity monitoring in smart homes or laboratories, replacing manual checking with a scheduled serverless pipeline. Electricity data is generated by virtual sensors, transmitted through AWS IoT Core, analyzed by Lambda, and stored centrally in DynamoDB. When energy waste is detected, the system can send near real-time email alerts.

- Operational Value:  
The dashboard allows users to monitor electricity consumption, view alert history, and download daily reports. Using AWS Serverless reduces the need for server management, simplifies deployment, and makes it easier to expand to more rooms, more devices, or real sensors in the future.

- Scalability:  
In the future, the system can be extended from virtual sensors to real sensors such as smart meters, ESP32, or IoT power measurement devices. It can also support electricity consumption trend analysis, anomaly prediction, device on/off schedule optimization, and an administration dashboard for multiple rooms or buildings.
![Architecture](/images/2-Proposal/2.architecture.png)