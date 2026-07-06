---
title : "Check Block Public Access"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.14.4. </b> "
---

#### Step 1: Open the Bucket

1. Click on the bucket: `energy-waste-report-347685737655-ap-southeast-1`
2. Select the **Permissions** tab.

#### Step 2: Verify Public Access Settings

1. Find the **Block public access (bucket settings)** section.
2. Verify the status: **Block all public access: On**
3. Find the **Bucket policy** section. Keep it in a state with no public bucket policy.
4. Find the **Access control list (ACL)** section. It must indicate that ACLs are disabled or Object Ownership is set to **Bucket owner enforced**.

#### Expected Results

- **Block all public access**: `On`
- **Bucket policy**: No public policy
- **ACLs**: `Disabled`

![Check Block Public Access](/images/5-Workshop/5.14-s3-report/5.14.4-public-access.png)