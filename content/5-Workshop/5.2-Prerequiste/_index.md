---
title : "Prerequisites"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

# Prerequisites

Before deploying the Smart Home Energy Waste Monitoring & Alert System, it is important to configure the AWS environment correctly. One of the most important preparations is selecting the correct AWS Region.

Since AWS resources are regional, every service you create—including AWS Lambda, Amazon DynamoDB, Amazon SNS, Amazon S3, AWS IoT Core, Amazon Cognito, and Amazon API Gateway—will only exist in the currently selected Region.

Throughout this Workshop, **Asia Pacific (Singapore)** (`ap-southeast-1`) will be used consistently. Using the same Region ensures that every AWS service can communicate correctly while avoiding unnecessary deployment errors and additional cross-region costs.

---

# Select the AWS Region

AWS allows users to choose the active Region from the navigation bar at the top of the AWS Management Console.

Follow these steps:

1. Open the **AWS Management Console**.
2. Look at the **upper-right corner** of the page.
3. Find the Region currently displayed.
4. Click the Region name.
5. From the Region list, select:

   **Asia Pacific (Singapore)**

6. Wait for the Console to refresh.
7. Verify that the selected Region displays either:

   **Singapore**

   or

   **Asia Pacific (Singapore)**

The following figure illustrates how to change the AWS Region.

![Select Region](/images/5-Workshop/5.2-Prerequisite/prerequisite1.png)

---

# Set Singapore as the Default Region

To prevent accidentally creating AWS resources in another Region after logging in again, AWS provides **Unified Settings**, allowing users to define a default Region for the Management Console.

Setting the default Region helps maintain consistency throughout the workshop and minimizes deployment mistakes.

Follow these steps:

1. Click the **Settings (Gear)** icon in the AWS Console.
2. Select **See all user settings**.
3. Locate the **Localization and default Region** section.
4. Click **Edit**.
5. Under **Default Region**, choose:

   **Asia Pacific (Singapore)**

6. Save the changes.

Once configured, newly opened AWS Console sessions will automatically use the Singapore Region.

The following figure demonstrates how to configure the default AWS Region.

![Default Region](/images/5-Workshop/5.2-Prerequisite/prerequisite2.png)

---

### Expected Result

After completing this prerequisite:

- The AWS Console is configured to use the **Asia Pacific (Singapore)** Region.
- All AWS resources created during the Workshop will be deployed in the same Region.
- Cross-region deployment issues are avoided.
- Resource management becomes simpler and more consistent throughout the project.