---
title : "Lambda Report Generator"
date : 2024-01-01
weight : 15
chapter : false
pre : " <b> 5.15. </b> "
---

#### Overview

In this section, you will create and configure the **Lambda Report Generator**. This function is responsible for fetching data from DynamoDB, aggregating it, and generating daily energy consumption reports to be stored in S3.

#### Content

- [Create Lambda Report Generator](5.15.1-create-lambda/)
- [Configure Timeout and Memory](5.15.2-config-timeout-memory/)
- [Configure Environment Variables](5.15.3-config-env-vars/)
- [Grant IAM Permissions](5.15.4-grant-iam-permissions/)
- [Deploy Source Code](5.15.5-deploy-source-code/)
- [Create Test Event](5.15.6-create-test-event/)
- [Verify S3 Output](5.15.7-check-s3-file/)
- [Verify DynamoDB Metadata](5.15.8-check-ddb-metadata/)
- [Create Daily Schedule](5.15.9-create-daily-schedule/)
- [Disable Schedule](5.15.10-disable-schedule/)