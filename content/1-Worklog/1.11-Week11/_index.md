---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---


## Week 11 Objectives

* Deploy the Report Generator module using AWS Serverless architecture.
* Integrate AWS Lambda with Amazon DynamoDB and Amazon S3.
* Strengthen IAM security by applying the Least Privilege principle.
* Focus on implementing production-ready code instead of completing additional Labs.

---

## Tasks Completed This Week

| Task | Result |
|------|--------|
| AWS Lambda Configuration | Created the **energy-report-generator** Lambda function using Python. Optimized memory allocation and timeout settings to improve report generation performance while maintaining cost efficiency. |
| Environment Variables | Configured environment variables for DynamoDB tables, Amazon S3 buckets, report prefixes, and application settings to eliminate hardcoded configurations and simplify deployment across multiple environments. |
| IAM Security Configuration | Implemented IAM Execution Roles following the Least Privilege principle. Granted only the required DynamoDB Query, PutItem, Amazon S3 PutObject, and CloudWatch logging permissions. |
| Serverless Report Generation | Developed the Report Generator workflow that retrieves data from DynamoDB, generates JSON reports, and automatically stores the generated reports in Amazon S3. |
| Security Optimization | Reviewed Lambda permissions, configuration management, and logging strategy to ensure the module complies with AWS security best practices. |

---

## Achievements

* Successfully completed the Serverless Report Generator module.
* Integrated AWS Lambda, DynamoDB, and Amazon S3 into a complete reporting workflow.
* Eliminated hardcoded configuration values using Environment Variables.
* Applied IAM Least Privilege to secure AWS resources.
* Improved knowledge of Serverless application deployment and security architecture.

---

## Evaluation

* Successfully achieved all objectives for Week 11.
* The Report Generator module is production-ready and follows AWS Serverless best practices.
* Security, maintainability, and deployment flexibility were significantly improved through proper IAM policies and environment-based configuration.

---

## Plan for Next Week

* Perform a complete end-to-end system validation.
* Prepare the final presentation slides and project demonstration.
* Organize source code, deployment documentation, and cleanup scripts.
* Review the complete AWS architecture before project submission.