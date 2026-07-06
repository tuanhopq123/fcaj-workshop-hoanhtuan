---
title : "Configure CORS"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.12.6. </b> "
---

The dashboard runs at `http://localhost:3000`, while the API Gateway uses a different domain. Therefore, CORS is required to allow the browser to make API requests.

#### Execution Steps

1. **Open CORS**: In the left menu, select **Develop** -> **CORS**. Click **Configure** (or **Edit**).
2. **Allow origins**: Enter `http://localhost:3000` (Note: Do not include a trailing slash). Click **Add** if required.
3. **Allow headers**: Add `authorization` and `content-type`. Click **Add** after each.
4. **Allow methods**: Select **GET** and **OPTIONS**.
5. **Expose headers**: Leave empty.
6. **Max age**: Enter `300`.
7. **Allow credentials**: Keep **Off** (or leave unchecked).
8. **Save**: Click **Save**.

![Configure CORS](/images/5-Workshop/5.12-api-gateway/5.12.6-configure-cors.png)