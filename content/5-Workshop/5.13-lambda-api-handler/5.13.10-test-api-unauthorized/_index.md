---
title : "Test API Without JWT"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b> 5.13.10. </b> "
---

Since all five routes are protected by the JWT Authorizer, opening the route directly in a browser without sending a token must be rejected.

#### Execution Steps

1. Navigate to: **API Gateway** -> **Stages** -> `$default`.
2. Copy the **Invoke URL**.
3. Append `/rooms` to the URL. Example: `https://<API-ID>.execute-api.ap-southeast-1.amazonaws.com/rooms`
4. Open the URL in a new tab.

#### Expected Result
You should receive:
- `401 Unauthorized` 
- OR: `{ "message": "Unauthorized" }`

*Note: This is the correct result, proving that the JWT Authorizer is blocking requests without tokens before they reach the Lambda function. Do not remove the authorizer to avoid the 401 error. Verification with a valid JWT will be performed once the Next.js dashboard logs in via Cognito.*

![Test API Without JWT](/images/5-Workshop/5.13-lambda-api-handler/5.13.10-test-unauthorized.png)