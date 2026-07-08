---
title: "5.6. Build the Energy Waste Detector Lambda"
date: 2026-07-01T18:00:00+07:00
draft: false
weight: 6
categories: ["Workshop"]
description: "Overview of building an AWS Lambda function that detects energy waste, stores telemetry in DynamoDB, and sends alerts via SNS."
---

AWS Lambda hosts the `energy-waste-detector` function, which processes incoming telemetry, decides whether energy is being wasted, stores the result in DynamoDB, and publishes an alert to SNS when needed.

In this section, we will perform eight main steps:

### 1. [Open AWS Lambda](5.6.1-open-lambda/)
Instructions on how to access the AWS Lambda console and start creating a function.

### 2. [Create the energy-waste-detector Function](5.6.2-create-function/)
Step-by-step guidance to create the Lambda function using the Python 3.14 runtime.

### 3. [Add Environment Variables](5.6.3-add-environment-variables/)
How to configure the `DDB_TABLE`, `SNS_TOPIC_ARN`, and `POWER_THRESHOLD_W` environment variables.

### 4. [Configure IAM Permissions for Lambda](5.6.4-configure-iam-permissions/)
How to grant the function permission to write to DynamoDB and publish to SNS, and how to add the function code.

### 5. [Test the Lambda Waste Detector](5.6.5-test-lambda-function/)
How to create and run a test event that simulates an energy waste scenario.

### 6. [Check the Test Result](5.6.6-check-test-result/)
How to verify that the test execution succeeded and returned the expected response.

### 7. [Check DynamoDB](5.6.7-check-dynamodb/)
How to confirm that new telemetry and alert items were stored in the table.

### 8. [Check the Alert Email](5.6.8-check-alert-email/)
How to verify that the energy waste alert email was received.
