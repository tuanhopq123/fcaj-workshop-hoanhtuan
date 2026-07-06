---
title : "Create S3 Report Bucket"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.14.1. </b> "
---

#### Step 1: Open Amazon S3

1. Check the top right corner to ensure the region is: **Asia Pacific (Singapore)**
2. In the AWS Console search bar, enter: `S3`
3. Select: **Amazon S3**
4. In the left menu, select: **General purpose buckets** *(Note: Some interfaces might just show "Buckets")*.
5. Click: **Create bucket**

#### Step 2: Choose Bucket Type

- For **Bucket type**, select: `General purpose`
- *(Do not select directory bucket).*

#### Step 3: Enter Bucket Name

- For **Bucket name**, enter exactly: `energy-waste-report-347685737655-ap-southeast-1`

*Note: S3 general purpose bucket names share a global namespace and must be unique. Appending the Account ID and Region reduces the chance of naming conflicts. If AWS shows the error "Bucket with the same name already exists", check if that bucket is already in your account. Do not arbitrarily create multiple buckets with similar names.*

#### Step 4: Choose Region

- For **AWS Region**, select: `Asia Pacific (Singapore) ap-southeast-1`
- *(Do not select Bangkok, Tokyo, or Virginia).*