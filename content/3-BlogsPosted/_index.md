---
title: "Blogs Posted"
date: 2026-07-06
weight: 3
chapter: false
pre: " <b> 3. </b> "
---
This section will list and introduce the technical blogs I have shared regarding cloud security, data engineering automation, and identity management on AWS.

###  [Blog 1 - SUBDOMAIN TAKEOVER: SECURITY RISKS FROM "DANGLING DNS" RECORDS ON AWS](3.1-Blog1/)
This article warns about the dangerous vulnerability known as Subdomain Takeover, which arises from dangling DNS records left behind after deprovisioning AWS resources (like S3 buckets or CloudFront distributions) without removing their corresponding Route 53 entries. It also highlights key defense strategies, including synchronized infrastructure lifecycle management, leveraging Alias Records, and building automated scanning scripts using AWS Lambda.

###  [Blog 2 - AUTOMATING DMS MIGRATION TROUBLESHOOTING (ORACLE ➡️ REDSHIFT) WITH AWS DEVOPS AGENT](3.2-Blog2/)
This blog focuses on optimizing Root Cause Analysis (RCA) when large-scale data migration pipelines encounter failure or high latency. The proposed design shifts from reactive troubleshooting to an automated workflow by combining CloudWatch Alarms with EventBridge, Lambda, and AWS DevOps Agent to autonomously investigate logs/metrics deep within Oracle and Redshift, providing immediate remediation recommendations.

###  [Blog 3 - SECURING AI AGENTS ON AWS WITH AUTH0 AND AMAZON BEDROCK AGENTCORE](3.3-Blog3/)
This post analyzes the security challenges of deploying AI Agents and introduces a joint solution combining Auth0 and Amazon Bedrock AgentCore. By adopting an Identity-First architecture, the system enforces robust user authentication via OIDC, manages temporary access through the Auth0 Token Vault, applies Fine-Grained Authorization (FGA), and integrates Human-in-the-loop (CIBA) mechanisms to ensure maximum security in production environments.