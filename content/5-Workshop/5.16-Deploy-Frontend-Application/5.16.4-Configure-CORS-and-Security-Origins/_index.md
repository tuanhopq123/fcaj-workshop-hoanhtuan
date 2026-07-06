---
title : "Configure CORS and Security Origins"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.16.4. </b> "
---

#### Step 1: Locate Amplify App Domain

1. After the Amplify deployment pipeline completes successfully, copy your live application URL from the Amplify Hosting dashboard (e.g., `https://main.d2ppdnlr5ik3e8.amplifyapp.com`).

#### Step 2: Update CORS Settings in API Gateway / Lambda

1. Return to your backend configurations (API Gateway or Lambda functions handling authentication/data streams).
2. Navigate to the **CORS** or security settings pane.
3. Under **Access-Control-Allow-Origin** (Allow origins), add your Amplify app domain link to authorize cross-origin resource sharing requests.
4. Save the configuration to ensure the frontend can communicate with backend resources securely without hitting CORS errors.

*(Note: Refer to your specific layout configuration screenshot `Allow origins.png` for reference).*