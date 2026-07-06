---
title : "Get API Gateway Invoke URL"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.16.1. </b> "
---

#### Step 1: Open API Gateway Console

1. In the AWS Console search bar, enter: `API Gateway`
2. Select the **API Gateway** service.
3. In the APIs dashboard, click on your project's API: `energy-waste-http-api`.

#### Step 2: Copy the Invoke URL

1. In the left navigation pane, under the **Deploy** section, choose **Stages**.
2. Select the **$default** stage from the stages list.
3. In the **Stage details** section, locate the **Invoke URL**.
4. Copy the complete URL string. This will serve as the backend API endpoint for your frontend application.

![API Gateway Invoke URL](/images/5-Workshop/5.16/API-Gateway-Invoke-URL.png)