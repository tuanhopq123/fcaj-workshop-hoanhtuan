---
title : "Check Encryption and Versioning"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.14.5. </b> "
---

#### Step 1: Open Properties Tab

1. Inside your bucket, select the **Properties** tab.

#### Step 2: Verify Versioning

1. Find the **Bucket Versioning** section.
2. The expected result must be: **Disabled**

#### Step 3: Verify Default Encryption

1. Find the **Default encryption** section.
2. The expected result must be:
   - **Server-side encryption with Amazon S3 managed keys**
   - **SSE-S3**

*Note: No modifications are needed if both settings are correct.*

![Check Encryption and Versioning](/images/5-Workshop/5.14-s3-report/5.14.5-encryption-versioning.png)