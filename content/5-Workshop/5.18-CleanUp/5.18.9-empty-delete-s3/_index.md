---
title: "5.18.9. Empty and Delete Amazon S3 Report Bucket"
date: 2026-07-07
weight: 9
---

Amazon S3 only allows a bucket to be deleted if it is completely empty. The Empty operation deletes all internal files permanently.

#### Step 1: Empty the Bucket
1. Open the **Amazon S3 Console** and go to the **General purpose buckets** list.
2. Check the box next to your project reporting bucket.
3. Click the **Empty** button.
4. Confirm by typing the bucket name as requested and click **Empty**.
5. Wait for the success page to show the process is finished. Do not close the browser while execution is active.

![Empty S3 Bucket](/images/5-Workshop/5.18-CleanUp/Picture5.png)
![S3 Bucket Empty Status](/images/5-Workshop/5.18-CleanUp/Picture6.png)

#### Step 2: Delete the Bucket Container
1. Go back to the **General purpose buckets** list directory.
2. Check the box next to the emptied reporting bucket and click **Delete**.
3. Type the exact name of the target bucket to verify.
4. Click **Delete bucket** and confirm it no longer appears in your resource list.

![Delete S3 Bucket](/images/5-Workshop/5.18-CleanUp/Picture7.png)
![S3 Bucket List Cleared](/images/5-Workshop/5.18-CleanUp/Picture8.png)