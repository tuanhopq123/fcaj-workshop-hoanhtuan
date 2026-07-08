---
title : "Update API Gateway CORS"
date : 2026-07-05
weight : 11
chapter : false
pre : " <b> 5.16.11 </b> "
---

Go to:

**API Gateway → APIs → energy-waste-http-api → CORS → Edit**

Configure:

**Allow origins**
```
http://localhost:3000
https://main.d2ppdnlr5ik3e8.amplifyapp.com
```
Do not add a trailing `/` to the domain.

**Allow headers**
```
authorization
content-type
```

**Allow methods**
```
GET
OPTIONS
```

**Expose headers**: leave empty.

**Max age**: `300`

**Allow credentials**: `Off`

Click **Save**.

![API Gateway CORS configuration](/images/5-Workshop/5.16/pic9.png)

## Result

With the frontend deployed on Amplify and CORS configured on API Gateway, the dashboard loads live data from DynamoDB via the Lambda/API Gateway backend after signing in with Cognito.

![Energy monitoring dashboard result](/images/5-Workshop/5.16/pic11.png)

![Waste alerts and reports result](/images/5-Workshop/5.16/pic12.png)
