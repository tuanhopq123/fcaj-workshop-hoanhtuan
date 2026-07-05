---
title : "Attach JWT Authorizer to Routes"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.12.5. </b> "
---

The JWT Authorizer only protects the routes to which it is attached. Any request lacking a valid token will be rejected by the API Gateway before it ever reaches the backend.

#### Execution Steps

1. Stay in the **Develop** -> **Authorization** page.
2. Locate the list of routes.
3. Select: `GET /rooms`
4. Click: **Attach authorizer**.
5. Select: `energy-waste-jwt-authorizer`
6. Leave the **Authorization scopes** section empty.
7. Click **Attach authorizer** (or **Save**).
8. Repeat these steps for all remaining routes:
   - `GET /telemetry`
   - `GET /alerts`
   - `GET /reports`
   - `GET /reports/{date}`

![Attach JWT Authorizer](/images/5-Workshop/5.12-api-gateway/5.12.5-attach-authorizer.png)