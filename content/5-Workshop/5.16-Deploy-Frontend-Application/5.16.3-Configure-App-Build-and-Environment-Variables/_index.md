---
title : "Configure App Build and Environment Variables"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.16.3. </b> "
---

#### Step 1: Add Repository and Branch

1. Select your frontend repository and the target branch (e.g., `main` or `master`) that contains your Next.js application code.
2. Click **Next**.

#### Step 2: Configure App Settings & Build Variables

1. On the **App settings** page, review the automatically detected build settings.
2. Expand the **Advanced settings** or **Environment variables** section.
3. Add your environment variables required for deployment, making sure to paste the API Gateway **Invoke URL** copied earlier into your API configuration variable.
4. Review the final setup and click **Save and deploy**.

*(Note: Refer to your specific build workflow screenshots such as `AWS-Amplify-Build-settings32.png` and `04-amplify-build-deployed.png` to verify successful continuous deployment pipeline progression).*