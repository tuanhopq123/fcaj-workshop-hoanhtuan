---
title: "5.16. Deploy Frontend Application"
date: 2026-07-06T20:30:00+07:00
draft: false
weight: 16
description: "Overview of deploying the Next.js frontend application using AWS Amplify and integrating backend APIs."
---

AWS Amplify Hosting is utilized to deploy, secure, and scale the frontend application automatically, allowing users to interact with real-time smart home metrics seamlessly.

In this section, we will perform eleven main steps:

### 1. [Get API Gateway Invoke URL](5.16.1-invoke-url/)
Instructions on how to access the API Gateway console and copy the default deployment stage endpoint for frontend integration.

### 2. [Create the Next.js Project](5.16.2-create-nextjs-project/)
Step-by-step guidance to scaffold the Next.js application and install the AWS Amplify library.

### 3. [Create the .env.local File](5.16.3-env-file/)
Instructions on securely storing the Cognito and API Gateway configuration values as local environment variables.

### 4. [Configure Amplify to Connect to Cognito](5.16.4-configure-amplify/)
Guidance to configure the AWS Amplify client-side library so the frontend can authenticate against the Cognito User Pool.

### 5. [Configure CSS and Layout](5.16.5-css-layout/)
Setting up the global stylesheet and root layout of the application.

### 6. [Create the JWT Fetch and API Gateway Call Function](5.16.6-api-helper/)
Building a reusable helper that retrieves the Cognito JWT token and calls the backend API Gateway endpoints.

### 7. [Create the Dashboard Interface](5.16.7-dashboard-ui/)
Building the main dashboard component that displays rooms, telemetry, alerts, and reports.

### 8. [Create the Login Page and Check the Cognito Session](5.16.8-login-page/)
Implementing the sign-in form and session validation logic that renders the Dashboard once authenticated.

### 9. [Push the Project to GitHub](5.16.9-push-github/)
Committing and pushing the completed source code to the GitHub repository.

### 10. [Create the AWS Amplify Hosting App](5.16.10-amplify-hosting/)
Step-by-step guidance to connect the GitHub repository branch with the AWS Amplify Hosting platform, configure build settings and environment variables, and deploy the app.

### 11. [Update API Gateway CORS](5.16.11-cors-config/)
Granting Cross-Origin Resource Sharing (CORS) permissions on the backend infrastructure for the newly generated Amplify production domain, and verifying the final result.
