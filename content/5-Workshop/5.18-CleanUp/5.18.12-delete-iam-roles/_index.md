---
title: "5.18.12. Delete Lambda IAM Execution Roles"
date: 2026-07-07
weight: 12
---

Execution Roles automatically created by the console are retained as standalone IAM identities even after their parent Lambda functions are destroyed.

#### 12.1. Open IAM Roles Dashboard
1. Search for **IAM** in the global console bar and open it.
2. In the left management tree pane, select **Roles**.

#### 12.2. Query Project Target Role Profiles
Search and filter execution role components using the following project profile descriptors one by one:
* `energy-waste-detector`
* `energy-virtual-sensor`
* `energy-api-handler`
* `energy-report-generator`
* `energy-virtual-sensor-every-minute`
* `energy-daily-report`

#### 12.3. Delete Each Individual Role
For each identified matching role candidate instance:
1. Click the specific unique Role name link text path to inspect its properties.
2. Check the **Last activity** and policy metrics parameters to confirm it belongs exclusively to this project ecosystem workspace.

![Inspect IAM Role Properties](/images/5-Workshop/5.18-CleanUp/Picture13.png)

3. Go back to the main **Roles** directory.
4. Check the row checkbox selector for the target role resource and click **Delete**.
5. Type the exact role identifier string into the validation input pop-up field and click **Delete**.

![Confirm IAM Role Deletion](/images/5-Workshop/5.18-CleanUp/Picture14.png)