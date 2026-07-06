---
title: "5.16. Deploy Frontend Application"
date: 2026-07-06T20:30:00+07:00
draft: false
weight: 560
description: "Overview of deploying the Next.js frontend application using AWS Amplify and integrating backend APIs."
---

AWS Amplify Hosting is utilized to deploy, secure, and scale the frontend application automatically, allowing users to interact with real-time smart home metrics seamlessly.

In this section, we will perform six main steps:

### 1. [Get API Gateway Invoke URL](5.16.1-Get-API-Gateway-Invoke-URL/)
Instructions on how to access the API Gateway console and copy the default deployment stage endpoint for frontend integration.

### 2. [Initialize Amplify Application](5.16.2-Initialize-Amplify-Application/)
Step-by-step guidance to connect your Git source code provider repository branch with the AWS Amplify Hosting platform.

### 3. [Configure App Build and Environment Variables](5.16.3-Configure-App-Build-and-Environment-Variables/)
Instructions on configuring advanced build steps and securely injecting backend base API URLs into the environment setup.

### 4. [Configure CORS and Security Origins](5.16.4-Configure-CORS-and-Security-Origins/)
Guidance to grant Cross-Origin Resource Sharing (CORS) permissions on the backend infrastructure for the newly generated Amplify production domain.

### 5. [Access Hosted Login Interface](5.16.5-Access-Hosted-Login-Interface/)
Verification of the publicly deployed application URL and testing the structural layout of the Cognito-integrated authentication interface.

### 6. [System Dashboard Verification](5.16.6-System-Dashboard-Verification/)
Final operational checks to ensure successful user login data stream validation and real-time visualization on the core telemetry monitoring dashboard.