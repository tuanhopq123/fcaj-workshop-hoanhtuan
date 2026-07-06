---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** into your report, including this warning.
{{% /notice %}}

## Week 6 Objectives

* Integrate a centralized logging and monitoring system into the application.
* Perform end-to-end testing of the Serverless application workflow.
* Complete hands-on labs on AWS Security Hub, AWS Lambda, and AWS resource management using Tags.

---

## Tasks Completed This Week

| Task | Result |
|------|--------|
| Amazon CloudWatch | Integrated Amazon CloudWatch to collect logs from AWS Lambda and API Gateway. Configured Metric Filters and CloudWatch Alarms to monitor system errors and send notifications through Amazon SNS when abnormal events occur. |
| System Testing | Performed end-to-end testing using Postman to validate APIs responsible for processing virtual sensor data, energy waste alerts, and reporting functions. Verified DynamoDB data consistency against CloudWatch logs. |
| Lab 18 - AWS Security Hub | Enabled and configured AWS Security Hub to evaluate the AWS account against recognized security standards, including AWS Foundational Security Best Practices and CIS Benchmarks. |
| Lab 22 - Optimizing EC2 Costs with Lambda | Implemented an automated solution using AWS Lambda and IAM Roles to schedule EC2 instance start and stop operations, improving cost efficiency and resource management. |
| Lab 27 - Resource Tags & Resource Groups | Practiced assigning Tags to AWS resources and organizing them using AWS Resource Groups to simplify resource management and automation across environments. |

---

## Achievements

* Successfully integrated Amazon CloudWatch into the Serverless application.
* Established centralized logging, monitoring, and automated alert mechanisms.
* Completed end-to-end testing across API Gateway, AWS Lambda, and Amazon DynamoDB.
* Strengthened understanding of centralized cloud security using AWS Security Hub.
* Improved knowledge of cloud cost optimization and AWS resource organization through Lambda automation and resource tagging.

---

## Evaluation

* Successfully achieved all objectives for Week 6.
* The Smart Home Energy Waste Monitoring system now includes a complete monitoring and observability layer.
* The hands-on labs significantly enhanced my understanding of cloud security, observability, and cost optimization following AWS best practices.

---

## Plan for Next Week

* Prepare the complete deployment documentation for the project.
* Develop deployment procedures and resource cleanup guidelines.
* Continue completing the remaining AWS hands-on labs according to the internship roadmap.