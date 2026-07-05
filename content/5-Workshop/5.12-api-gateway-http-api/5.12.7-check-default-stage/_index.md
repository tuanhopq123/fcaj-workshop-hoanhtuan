---
title : "Check $default Stage"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.12.7. </b> "
---

The stage is the deployment endpoint. Since the `$default` stage has **Auto-deploy** enabled, API changes are deployed automatically.

#### Execution Steps

1. In the left menu, select: **Deploy** -> **Stages**.
2. Select the stage: `$default`
3. Verify: **Auto-deploy: Enabled**
4. Locate and copy the **Invoke URL**. 
   - The URL follows this format: `https://<API-ID>.execute-api.ap-southeast-1.amazonaws.com`
   - *Note: Since we use `$default`, route URLs will be accessed like: `https://<API-ID>.execute-api.ap-southeast-1.amazonaws.com/rooms`.*

*Note: Do not click the orange **Deploy** button. Changes are deployed automatically.*

![Check $default Stage](/images/5-Workshop/5.12-api-gateway/5.12.7-check-stage.png)