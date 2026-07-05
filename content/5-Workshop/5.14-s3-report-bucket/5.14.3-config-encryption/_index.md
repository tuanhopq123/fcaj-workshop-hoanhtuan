---
title : "Configure Encryption & Create Bucket"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.14.3. </b> "
---

#### Step 1: Default Encryption

1. Under the **Default encryption** section, choose or keep:
   - **Server-side encryption with Amazon S3 managed keys (SSE-S3)**
2. Do **not** select `AWS Key Management Service key (SSE-KMS)` because this project does not require a customer-managed KMS key.

*Note: Amazon S3 currently automatically encrypts objects using SSE-S3 by default. However, you should still verify this in the Console to ensure the bucket uses SSE-S3 as designed. If there is a section related to **S3 Bucket Key**, no configuration is needed since Bucket Keys are primarily relevant to SSE-KMS.*

![Configure Encryption](/images/5-Workshop/5.14-s3-report/5.14.3-encryption.png)

#### Step 2: Advanced Settings

1. Keep **Object Lock**: **Disable**

*Note: Do not enable Object Lock because the project does not require mandatory deletion protection (WORM), and enabling Object Lock requires versioning to be enabled first.*

![Advanced Settings - Object Lock](/images/5-Workshop/5.14-s3-report/5.14.3-object-lock.png)

#### Step 3: Create Bucket

1. Perform a final review of your configurations:
   - **Bucket name**: `energy-waste-report-347685737655-ap-southeast-1`
   - **Region**: `ap-southeast-1`
   - **Object Ownership**: `Bucket owner enforced`
   - **Block all public access**: `On`
   - **Bucket Versioning**: `Disabled`
   - **Default encryption**: `SSE-S3`
   - **Object Lock**: `Disabled`

2. Click **Create bucket**.
3. Wait for the success notification. *(The AWS Console creates the bucket after you complete the above settings and click the Create bucket button).*

![Create Bucket](/images/5-Workshop/5.14-s3-report/5.14.3-create-bucket.png)