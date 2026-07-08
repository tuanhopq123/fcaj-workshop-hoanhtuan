---
title: "5.7. Create Lambda Virtual Sensor"
date: 2026-07-05
draft: false
weight: 7
description: "Overview and structural routing for building a Lambda-based virtual sensor to simulate IoT power consumption data."
---

In this section, you will go through the following steps to build and test the virtual sensor:

#### [5.7.1 Create a Lambda Function](5.7.1-create-function.md)
Initialize the core AWS Lambda function environment utilizing the Python runtime.

#### [5.7.2 Configure Environment Variables](5.7.2-environment-variables/)
Set up dynamic configurations and isolated key-value pairs for flexible resource reference.

#### [5.7.3 Grant IAM Permissions](5.7.3-iam-permissions/)
Modify the execution role's policy to allow the function to publish telemetry data securely to AWS IoT Core.

#### [5.7.4 Deploy the Simulation Source Code](5.7.4-deploy-code/)
Implement and deploy the core Python simulation script that generates realistic equipment metrics.

#### [5.7.5 Create a Test Event](5.7.5-create-test-event/)
Define custom execution JSON payloads and configurations for targeted manual testing.

#### [5.7.6 Execute Test and Verify Results](5.7.6-execute-test/)
Trigger manual executions to validate the end-to-end system behavior and audit real-time output logs.