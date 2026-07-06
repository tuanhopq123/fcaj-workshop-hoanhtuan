---
title : "Create JWT Authorizer"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.12.4. </b> "
---

#### A. Open Authorization

1. Return to the API Gateway tab.
2. Ensure you are in the correct API: `energy-waste-http-api`.
3. In the left menu, select: **Develop** -> **Authorization**.
4. Locate the **Manage authorizers** section.
5. Click **Create** (or **Create authorizer**).

#### B. Configure Authorizer Details

1. **Authorizer name**: `energy-waste-jwt-authorizer`
2. **Authorizer type**: Select **JWT** (Do not select Lambda).
3. **Identity source**: Enter exactly: `$request.header.Authorization`
   - *Check:* Ensure the `$` sign is at the beginning, use dots between `request`, `header`, and `Authorization`, and capitalize 'A'.
4. **Issuer URL**: Paste the Issuer URL formatted as:
   `https://cognito-idp.ap-southeast-1.amazonaws.com/<USER_POOL_ID>`
   *(Example: `https://cognito-idp.ap-southeast-1.amazonaws.com/ap-southeast-1_AbCdEf123`)*
5. **Audience**: Paste the **App Client ID** of `energy-waste-dashboard-client`.
   - *Important:* If there is an **Add** button, ensure you click it after pasting. The value must appear in the list; simply typing it into the field is not enough to save it.
6. **Authorization scopes**: Leave empty.

![Configure Authorizer Details](/images/5-Workshop/5.12-api-gateway/5.12.4-configure-authorizer.png)

7. Click **Create**.

After clicking Create:

![Authorizer Created](/images/5-Workshop/5.12-api-gateway/5.12.4-authorizer-created.png)