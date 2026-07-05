---
title : "Attach Integration to Routes"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.13.8. </b> "
---

Now, we will attach the created integration to the five defined routes.

#### Execution Steps

1. In the left menu, select: **Routes**.
2. Select the route: `GET /rooms`
3. In the **Integration** section, click: **Attach integration**.
4. Select: `energy-api-handler-integration`
5. Click: **Attach integration**.
6. Repeat the same steps for:
   - `GET /telemetry`
   - `GET /alerts`
   - `GET /reports`
   - `GET /reports/{date}`

#### Expected Result

All five routes must have:
- **Authorization**: `energy-waste-jwt-authorizer`
- **Integration**: `energy-api-handler`

| Route | Authorizer | Integration |
| :--- | :--- | :--- |
| `GET /rooms` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /telemetry` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /alerts` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /reports` | `energy-waste-jwt-authorizer` | `energy-api-handler` |
| `GET /reports/{date}` | `energy-waste-jwt-authorizer` | `energy-api-handler` |

*Note: Since the `$default` stage has **Auto-deploy** enabled, there is no need to manually click the Deploy button.*

![Attach Integration to Routes](/images/5-Workshop/5.13-lambda-api-handler/5.13.8-attach-integration.png)