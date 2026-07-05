---
title : "Configure Environment Variables"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.13.3. </b> "
---

Environment Variables allow you to change the table name, default room, and data limit without modifying the source code. AWS allows you to configure this under **Configuration** -> **Environment variables**.

#### Execution Steps

1. Select: **Configuration** -> **Environment variables**
2. Click: **Edit**
3. Add the following four variables:

**Variable 1**
- Key: `DDB_TABLE`
- Value: `EnergyWasteData`

**Variable 2**
- Key: `DEFAULT_ROOM_ID`
- Value: `lab-01`

**Variable 3**
- Key: `DEFAULT_LIMIT`
- Value: `50`

**Variable 4**
- Key: `REPORTS_PK`
- Value: `REPORTS`

![Add Environment Variables](/images/5-Workshop/5.13-lambda-api-handler/5.13.3-add-env.png)

4. Click: **Save**

After saving:

![Environment Variables Saved](/images/5-Workshop/5.13-lambda-api-handler/5.13.3-env-saved.png)