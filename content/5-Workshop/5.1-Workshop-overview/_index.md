---
title : "Introduction"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

# Introduction

## Smart Home Energy Waste Monitoring & Alert System

As smart electrical devices become increasingly common in homes and businesses, monitoring power consumption and detecting energy waste have become essential requirements. Keeping electrical devices running when no one is present not only wastes electricity but also increases operating costs, reduces resource efficiency, and negatively impacts energy-saving initiatives.

The **Smart Home Energy Waste Monitoring & Alert System** is built on **Amazon Web Services (AWS)** to monitor electricity consumption in real time, automatically detect energy waste, and notify users whenever abnormal power usage is identified.

The entire system is implemented using a **Serverless Architecture**, leveraging fully managed AWS services to reduce operational costs, improve scalability, and eliminate the need for server management.

To simulate real-world scenarios, the system utilizes **Virtual Sensors** implemented with **AWS Lambda**. These virtual sensors periodically generate the following telemetry data:

- Voltage
- Current
- Power Consumption
- Device Status
- Occupancy Status

The system identifies an **energy waste event** when all of the following conditions are satisfied simultaneously:

- The electrical device remains turned on.
- No occupant is detected in the room.
- Power consumption exceeds the predefined threshold.

Once an energy waste event is detected, the system automatically:

- Stores telemetry data in Amazon DynamoDB.
- Records the alert information.
- Sends email notifications through Amazon SNS.
- Supports scheduled report generation for monitoring and data analysis.

---

# Workshop Objectives

After completing this workshop, participants will be able to:

- Understand how to build an IoT monitoring system using a Serverless architecture on AWS.
- Deploy and process sensor data with AWS IoT Core.
- Implement business logic using AWS Lambda.
- Store application data in Amazon DynamoDB.
- Send email notifications using Amazon SNS.
- Build RESTful APIs with Amazon API Gateway.
- Authenticate users with Amazon Cognito.
- Generate automated reports and store them in Amazon S3.
- Deploy a web application using AWS Amplify Hosting.
- Protect web applications with AWS WAF.

---

# Workshop Overview

In this workshop, we will build the complete **Smart Home Energy Waste Monitoring & Alert System** step by step using a Serverless architecture on AWS.

The overall system architecture consists of several functional workflows.

### Virtual Sensor Flow

Amazon EventBridge triggers the **Lambda Virtual Sensor** function every minute to generate simulated sensor data.

After the data is generated, it is published to **AWS IoT Core** using the MQTT protocol for further processing.

---

### Waste Detection Flow

AWS IoT Rules receive incoming sensor data from AWS IoT Core and forward it to the **Lambda Waste Detector** function.

The Lambda function analyzes the incoming telemetry to determine whether an energy waste situation has occurred.

If energy waste is detected, the system automatically:

- Stores telemetry data in Amazon DynamoDB.
- Records alert information.
- Sends email notifications to users through Amazon SNS.

---

### Authentication & API Flow

Users authenticate with the application using **Amazon Cognito**.

After successful authentication, requests from the web application are routed to **Amazon API Gateway**.

API Gateway invokes the **Lambda API Handler**, which retrieves data from Amazon DynamoDB and returns the response to the frontend application.

---

### Report Generation Flow

The **Lambda Report Generator** function is triggered on a scheduled basis to retrieve monitoring data from Amazon DynamoDB.

After processing the data, the function generates a JSON report and stores it in **Amazon S3** for long-term storage and download.

---

### Frontend Application

The frontend application is developed using **Next.js** and deployed with **AWS Amplify Hosting**.

All incoming HTTP/HTTPS traffic is protected by **AWS WAF**, helping mitigate common web application attacks while enhancing the overall security of the system.

---

# Overall System Architecture

The figure below illustrates the overall architecture of the **Smart Home Energy Waste Monitoring & Alert System** deployed on **Amazon Web Services (AWS)**.

The architecture provides a complete overview of the data processing workflow, beginning with virtual sensor simulation, followed by data collection, processing, energy waste detection, data storage, notification delivery, automated report generation, and finally data visualization through the web application.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)