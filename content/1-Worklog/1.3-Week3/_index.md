---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---


## Week 3 Objectives

- Configure the security foundation for the project using AWS IAM.
- Initialize the DynamoDB database for the Smart Home Energy Waste Monitoring System.
- Complete AWS IAM, Amazon VPC, and AWS Budget hands-on labs.

---

## Tasks Performed This Week

| Day | Task | Start Date | Completion Date |
|-----|------|------------|-----------------|
|2|Configure IAM Roles and Policies for AWS Lambda.|08/25/2025|08/25/2025|
|3|Create DynamoDB tables and prepare sample data.|08/26/2025|08/26/2025|
|4|Complete AWS IAM Lab.|08/27/2025|08/27/2025|
|5|Complete Amazon VPC Lab.|08/28/2025|08/28/2025|
|6|Complete AWS Budget Lab and review all completed work.|08/29/2025|08/29/2025|

---

## Week 3 Achievements

This week focused on establishing the project's security and database foundation while completing several AWS hands-on labs.

### Project Progress

The security layer of the project was successfully configured using AWS IAM.

IAM Roles and custom IAM Policies were created following the **Least Privilege Principle**, ensuring that the Lambda functions only have permission to access the required AWS resources.

Permissions were configured for:

- Amazon DynamoDB
- Amazon CloudWatch Logs
- Amazon S3 (for report storage)

The project's NoSQL database was also initialized using Amazon DynamoDB.

The following tables were prepared for the Smart Home Energy Waste Monitoring System:

- Rooms
- Telemetry
- Alerts
- Reports

Sample data was inserted into each table to support future API development and testing.

---

# AWS Hands-on Labs

## Lab 2 — AWS IAM

This lab focused on identity and access management within AWS. The exercises included creating IAM users, IAM groups, assigning permissions, and enabling Multi-Factor Authentication (MFA) to improve account security.

![IAM Group](/images/1-worklog/1.3-lab2-1.png)

![IAM User](/images/1-worklog/1.3-lab2-2.png)

![Permissions](/images/1-worklog/1.3-lab2-3.png)

![Policies](/images/1-worklog/1.3-lab2-4.png)

![Enable MFA](/images/1-worklog/1.3-lab2-5.png)

![Lab Completion](/images/1-worklog/1.3-lab2-6.png)

---

## Lab 3 — Amazon VPC

This lab introduced the fundamental concepts of AWS networking by building a Virtual Private Cloud (VPC).

The implementation included:

- Creating a VPC
- Configuring CIDR Blocks
- Creating Public and Private Subnets
- Configuring Route Tables
- Creating an Internet Gateway
- Configuring a NAT Gateway
- Verifying network connectivity

![VPC-1](/images/1-worklog/1.3-lab3-1.png)

![VPC-2](/images/1-worklog/1.3-lab3-2.png)

![VPC-3](/images/1-worklog/1.3-lab3-3.png)

![VPC-4](/images/1-worklog/1.3-lab3-4.png)

![VPC-5](/images/1-worklog/1.3-lab3-5.png)

![VPC-6](/images/1-worklog/1.3-lab3-6.png)

![VPC-7](/images/1-worklog/1.3-lab3-7.png)

![VPC-8](/images/1-worklog/1.3-lab3-8.png)

![VPC-9](/images/1-worklog/1.3-lab3-9.png)

![VPC-10](/images/1-worklog/1.3-lab3-10.png)

![VPC-11](/images/1-worklog/1.3-lab3-11.png)

![VPC-12](/images/1-worklog/1.3-lab3-12.png)

![VPC-13](/images/1-worklog/1.3-lab3-13.png)

![VPC-14](/images/1-worklog/1.3-lab3-14.png)

![VPC-15](/images/1-worklog/1.3-lab3-15.png)

![VPC-16](/images/1-worklog/1.3-lab3-16.png)

![VPC-17](/images/1-worklog/1.3-lab3-17.png)

![VPC-18](/images/1-worklog/1.3-lab3-18.png)

![VPC-19](/images/1-worklog/1.3-lab3-19.png)

![VPC-20](/images/1-worklog/1.3-lab3-20.png)

![VPC-21](/images/1-worklog/1.3-lab3-21.png)

![VPC-22](/images/1-worklog/1.3-lab3-22.png)

![VPC-23](/images/1-worklog/1.3-lab3-23.png)

---

## Lab 7 — AWS Budget

This lab focused on cloud cost management.

A monthly AWS Budget was created together with email notifications to ensure that AWS Free Tier resources and AWS Credits are used efficiently.

![Budget-1](/images/1-worklog/1.3-lab7-1.png)

![Budget-2](/images/1-worklog/1.3-lab7-2.png)

![Budget-3](/images/1-worklog/1.3-lab7-3.png)

![Budget-4](/images/1-worklog/1.3-lab7-4.png)

![Budget-5](/images/1-worklog/1.3-lab7-5.png)

---

## Learning Outcomes

After completing this week's activities, I gained a better understanding of:

- AWS Identity and Access Management.
- Secure permission management using IAM Roles and Policies.
- Virtual networking concepts with Amazon VPC.
- Cloud cost optimization using AWS Budget.
- Database initialization using Amazon DynamoDB.

---

## Week 3 Summary

- Completed the project's security configuration.
- Initialized the DynamoDB database.
- Finished AWS IAM Lab.
- Finished Amazon VPC Lab.
- Finished AWS Budget Lab.

---

## Plan for Next Week

- Develop AWS Lambda functions.
- Implement REST APIs.
- Connect Lambda with DynamoDB.
- Test CRUD operations.