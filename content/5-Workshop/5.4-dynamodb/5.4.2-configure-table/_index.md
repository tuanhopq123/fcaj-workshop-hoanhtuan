---
title : "Configure Table Details"
date : 2026-07-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

1. **Enter table details**
   * Table name: `EnergyWasteData`
   * Partition key: `PK`, type **String**
   * Sort key: `SK`, type **String**
   * Important: `PK` and `SK` must be uppercase (not `pk`, `sk`, `roomId`, `id`), because the Lambda code later will use exactly `PK` and `SK`.

![Create table - table details](/images/5-Workshop/5.4-dynamodb/pic3.png)

2. **Customize table settings**
   * Scroll down to **Table settings** and select **Customize settings**.
   * Under **Capacity mode**, choose **On-demand** (no need to configure fixed read/write capacity for this demo, and it requires fewer steps for a workshop).
   * Leave the remaining sections at their defaults: no secondary indexes, default encryption, deletion protection off, tags optional.
   * If a **Table class** section appears, choose **DynamoDB Standard**.

![Table settings - Capacity mode](/images/5-Workshop/5.4-dynamodb/pic4.png)

3. **Create the table**
   * Click **Create table** and wait for the confirmation message.

![EnergyWasteData table created successfully](/images/5-Workshop/5.4-dynamodb/pic5.png)
