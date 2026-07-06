---
title : "Create API Routes"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.12.2. </b> "
---

An HTTP API route consists of two components: the HTTP method and the resource path (e.g., `GET /rooms`). We need to create the following five routes:

- `GET /rooms`
- `GET /telemetry`
- `GET /alerts`
- `GET /reports`
- `GET /reports/{date}`

#### Execution Steps

1. In the left menu, select: **Develop** -> **Routes**.
2. In the **Routes for energy-waste-http-api** section, click **Create**.
3. Create each route by filling in the **Method** and **Path** as specified below:

| Method | Path |
| :--- | :--- |
| **GET** | `/rooms` |
| **GET** | `/telemetry` |
| **GET** | `/alerts` |
| **GET** | `/reports` |
| **GET** | `/reports/{date}` |

*Note: For the last route, ensure you keep the curly braces: `{date}`.*

4. After creating, verify that all five routes appear in the left-hand route list.

![Create API Routes](/images/5-Workshop/5.12-api-gateway/5.12.2-create-routes.png)