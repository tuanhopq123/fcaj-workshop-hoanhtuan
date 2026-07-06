---
title : "Lambda API Handler"
date : 2024-01-01
weight : 13
chapter : false
pre : " <b> 5.13. </b> "
---

#### Overview

In this section, you will create and configure the **Lambda API Handler**. This function is responsible for processing requests from the API Gateway and interacting with DynamoDB to fetch energy waste reports and telemetry data.

#### Content

- [Create Lambda API Handler](5.13.1-create-lambda/)
- [Adjust Timeout](5.13.2-adjust-timeout/)
- [Configure Environment Variables](5.13.3-config-env-vars/)
- [Grant DynamoDB Read Permissions](5.13.4-grant-ddb-permissions/)
- [Deploy Source Code](5.13.5-deploy-source-code/)
- [Test Lambda Directly](5.13.6-test-lambda-directly/)
- [Create Lambda Integration in API Gateway](5.13.7-create-lambda-integration/)
- [Attach Integration to Routes](5.13.8-attach-integration-to-routes/)
- [Verify API Gateway Permissions on Lambda](5.13.9-check-resource-policy/)
- [Test API Without JWT](5.13.10-test-api-unauthorized/)