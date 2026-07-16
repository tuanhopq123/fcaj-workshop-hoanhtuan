---
title: "Week 2 Worklog"
date: 2026-04-24
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---


### Week 2 Objectives

- Study the final project requirements and evaluation rubric.
- Analyze the project requirements and design the overall system architecture.
- Prepare a bilingual project proposal.
- Define the AWS services required for the Smart Home Energy Waste Monitoring & Alert System.

---

### Tasks to be carried out this week

| Day | Task                                                                                                                                  | Start Date | Completion Date | Reference Material             |
| --- | ------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------ |
| 1   | Studied the workshop requirements, evaluation rubric, and project guidelines provided by the AWS Workforce Bootcamp.                  | 24/04/2026 | 24/04/2026      | AWS Study Group                |
| 2   | Analyzed the project requirements and identified the AWS services required for the Smart Home Energy Waste Monitoring & Alert System. | 25/04/2026 | 25/04/2026      | AWS Documentation              |
| 3   | Designed the first version of the serverless solution architecture and defined the overall system workflow.                           | 26/04/2026 | 27/04/2026      | AWS Architecture Center        |
| 4   | Prepared the bilingual project proposal, including objectives, architecture, expected outcomes, and implementation roadmap.           | 28/04/2026 | 29/04/2026      | Project Guideline              |
| 5   | Reviewed and refined the architecture according to AWS Well-Architected Framework best practices before starting implementation.      | 30/04/2026 | 30/04/2026      | AWS Well-Architected Framework |


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
- Prepared all technical documents before beginning the deployment stage.

---

### Plan for Next Week

- Configure AWS IAM users, roles, and policies.
- Create Amazon DynamoDB tables.
- Design the database schema.
- Prepare sample data for testing.
- Begin implementing the first AWS services of the workshop.