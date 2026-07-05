---
title : "Prepare Amazon Cognito Information"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.12.3. </b> "
---

The JWT Authorizer requires two specific values: **User Pool ID** and **App Client ID**.

#### A. Retrieve User Pool ID

1. Open a new AWS Console tab.
2. Navigate to: **Amazon Cognito** -> **User pools** -> `energy-waste-user-pool` -> **Overview**.
3. Locate the **User pool ID**.
4. Click the copy icon. The value will look similar to: `ap-southeast-1_OiGmVapoL`
5. Paste this value temporarily into a Notepad.

![Retrieve User Pool ID](/images/5-Workshop/5.12-api-gateway/5.12.3-user-pool-id.png)

#### B. Retrieve App Client ID

1. Within the same user pool, select: **Applications** -> **App clients**.
2. Select: `energy-waste-dashboard-client`
3. Locate the **Client ID** (e.g., `42bod21u3a1g499u643mt056fm`).
4. Copy the Client ID and paste it into your Notepad.

*Note: Do not copy the **Client secret**. Your app client must display "Client secret: -".*

![Retrieve App Client ID](/images/5-Workshop/5.12-api-gateway/5.12.3-client-id.png)