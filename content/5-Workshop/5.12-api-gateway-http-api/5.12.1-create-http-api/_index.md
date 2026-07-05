---
title : "Create HTTP API"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.12.1. </b> "
---

#### Step 1: Open API Gateway

1. Check the Region: `Asia Pacific (Singapore) ap-southeast-1`
2. In the AWS Console search bar, enter: `API Gateway`
3. Select the **Amazon API Gateway** service.
4. Click **Create API**.
5. Find **HTTP API** and click **Build**.
   *(Do not select REST API, WebSocket API, or REST API Private. The HTTP API supports JWT authorizers natively and is ideal for serverless architectures).*

#### Step 2: Configure API Details

- **API name**: `energy-waste-http-api`
- **IP address type**: `IPv4` *(If there is a 'Dualstack' option, it is not required for now).*
- **Integrations**: Skip adding integrations. Do not select `energy-virtual-sensor` or `energy-waste-detector` as these belong to the IoT workflow. If you see an **Add integration** button, skip it and click **Next**.

#### Step 3: Configure Routes

- On the **Configure routes** page, you do not need to add any routes yet.
- Click **Next**.

#### Step 4: Configure Stages

- Keep the stage name: `$default`
- Ensure **Auto-deploy** is set to **On**.
  *(The `$default` stage allows calling the API directly from the base URL without `/dev` or `/prod` prefixes. With Auto-deploy enabled, configuration changes are deployed automatically).*
- Click **Next**.

#### Step 5: Review and Create

- Review:
  - **API name**: `energy-waste-http-api`
  - **Protocol type**: `HTTP`
  - **IP address type**: `IPv4`
  - **Stage**: `$default`
  - **Auto-deploy**: `Enabled`
- Click **Create**.

**Result:**
You will see the **Overview** page for `energy-waste-http-api`. Note down your **API ID** and **Invoke URL**.

![Create HTTP API](/images/5-Workshop/5.12-api-gateway/5.12.1-create-http-api.png)