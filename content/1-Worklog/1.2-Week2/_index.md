---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy it verbatim** into your report, including this warning.
{{% /notice %}}

### Week 2 Objectives

- Study the final project requirements and evaluation rubric.
- Analyze the project requirements and design the overall system architecture.
- Prepare a bilingual project proposal.
- Define the AWS services required for the Smart Home Energy Waste Monitoring & Alert System.

---

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|------------|-----------------|-------------------|
| 2 | Study the final project rubric and understand the evaluation criteria. | 08/18/2025 | 08/18/2025 | AWS Study Group |
| 3 | Analyze project requirements and identify suitable AWS services for the system. | 08/19/2025 | 08/19/2025 | AWS Documentation |
| 4 | Design the overall serverless architecture of the project. | 08/20/2025 | 08/20/2025 | AWS Architecture Center |
| 5 | Prepare the bilingual project proposal (English & Vietnamese). | 08/21/2025 | 08/21/2025 | Project Guideline |
| 6 | Review the architecture, optimize the design, and prepare for implementation. | 08/22/2025 | 08/22/2025 | AWS Well-Architected Framework |

---

### Week 2 Achievements

During this week, the project direction was finalized and the overall solution architecture was completed.

The project was officially defined as:

**Smart Home Energy Waste Monitoring & Alert System using Virtual Sensors on AWS**

The system is designed to monitor electricity consumption in a smart home environment using virtual sensors. Sensor data is processed by AWS serverless services to detect abnormal energy usage and automatically generate alerts whenever energy waste is identified.

The overall architecture follows a fully serverless approach to achieve high scalability, lower operational costs, and simplified infrastructure management.

---

### Solution Architecture

The proposed architecture includes the following AWS services:

- Amazon API Gateway
- AWS Lambda
- Amazon DynamoDB
- Amazon S3
- Amazon CloudWatch
- AWS IAM

The application workflow is designed as follows:

1. Virtual sensors generate room and device data.
2. Requests are sent through Amazon API Gateway.
3. AWS Lambda processes business logic.
4. Data is stored in Amazon DynamoDB.
5. Logs and metrics are collected by Amazon CloudWatch.
6. Static resources and generated reports are stored in Amazon S3.
7. AWS IAM controls permissions using the Least Privilege principle.

### Initial System Architecture

The first version of the system architecture was completed during this week.

![System Architecture](/images/1-worklog/1.2-system-architecture.png)

---

### Project Progress

The bilingual project proposal was completed, including:

- Project overview
- Objectives
- Problem statement
- Proposed architecture
- AWS services
- System workflow
- Expected outcomes

In addition, possible testing approaches and deployment risks were analyzed to prepare for the implementation phase.

---

### Learning Outcomes

After completing this week's tasks, I gained a better understanding of:

- Designing a serverless architecture on AWS.
- Selecting appropriate AWS services for IoT-style applications.
- Cost optimization using the Pay-as-you-go pricing model.
- Applying the AWS Well-Architected Framework.
- Designing scalable and maintainable cloud systems.

---

### Week 2 Summary

- Completed the project proposal.
- Finished the first version of the architecture diagram.
- Selected six core AWS services.
- Defined the overall system workflow.
- Established the implementation roadmap for the following weeks.

---

### Plan for Next Week

- Configure IAM Roles and IAM Policies.
- Create DynamoDB tables.
- Design the database schema.
- Prepare sample data for testing.
- Begin implementing backend services using AWS Lambda.