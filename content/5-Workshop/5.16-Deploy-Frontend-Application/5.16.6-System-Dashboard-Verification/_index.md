---
title : "System Dashboard Verification"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.16.6. </b> "
---

#### Step 1: Log Into the Application

1. Enter valid Amazon Cognito User Pool credentials (User email and password) on the login page.
2. Click the **Sign in** button.

#### Step 2: Validate Real-Time Energy Tracking Data

1. Upon successful authentication, you will be redirected to the main dashboard interface.
2. Confirm the top application bar displays the logged-in user context (`Cognito authenticated`).
3. Check that the **Energy Monitoring Dashboard** successfully triggers API queries and fetches current metrics:
   - **Rooms:** Number of configured smart home labs.
   - **Telemetry:** Latest incoming metric samples count.
   - **Alerts:** Recent critical energy waste alerts.
   - **Reports:** Number of system-generated data summaries.
4. Verify the **Telemetry gần nhất** table updates dynamically with tracking logs showing Timestamp, Device name (`Air Conditioner`), Power consumption (`W`), Device State, Occupancy status, and Waste Analysis.

![Dashboard Interface](/images/5-Workshop/5.16/WED1.png)