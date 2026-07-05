---
title : "Check File in S3"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b> 5.15.7. </b> "
---

#### Step 1: Open S3 Bucket

1. Navigate to **Amazon S3**.
2. Select the bucket: `energy-waste-report-347685737655-ap-southeast-1`

#### Step 2: Open Report Prefix

1. In the **Objects** tab, open the folder: `reports`
2. Next, open the folder: `2026-07-03`
3. Verify that the following file exists: `energy-report-lab-01-2026-07-03.json`
4. The full path should be: `reports/2026-07-03/energy-report-lab-01-2026-07-03.json`

#### Step 3: Check Object Details

Click on the file and verify the following properties:
- **Type**: `json`
- **Content type**: `application/json`
- **Encryption**: `SSE-S3`
- The file size must be greater than **0 bytes**.

*Security Notes:*
- Do **not** click `Make public`.
- Do **not** turn off `Block all public access`.

![Check File in S3](/images/5-Workshop/5.15-lambda-report/5.15.7-s3-file.png)