---
title: "5.4.1 Configure Table Details & Settings"
weight: 1
description: "Set up core parameters including Partition key, Sort key, and Capacity mode for DynamoDB."
---

# 5.4.1 Configure Table Details

On the table creation page, proceed to fill in the core configuration details exactly as follows[cite: 1]:

### 1. Table Details
* **Table name:** `EnergyWasteData`[cite: 1]
* **Partition key:** `PK` (Data type: **String**)[cite: 1]
* **Sort key - optional:** `SK` (Data type: **String**)[cite: 1]

> ⚠️ **CRITICAL NOTE:** 
> You must capitalize **PK** and **SK** exactly as shown[cite: 1]. DO NOT write them as lower-case `pk`, `sk`, `roomId`, or `id`[cite: 1]. The backend Lambda function code will interact directly with these exact capitalized keys later on[cite: 1].

![Table Details Configuration](dynamodb-table-details.png)

---

### 2. Table Settings

Scroll down to configure advanced options optimized for this workshop environment[cite: 1]:

* Under **Table settings**, select **Customize settings**[cite: 1].
* Under **Table class**, select **DynamoDB Standard**[cite: 1].
* Under **Read/write capacity settings** ➔ **Capacity mode**, select: **On-demand**[cite: 1].

> 💡 **Why choose On-demand?** This demo project does not require pre-provisioned read/write capacity limits[cite: 1]. Selecting On-demand reduces configuration steps and fits perfectly for workshop execution[cite: 1].

![On-demand Capacity Mode Configuration](dynamodb-on-demand-settings.png)

### 3. Finalize Other Default Settings
* **Secondary indexes:** Leave blank (Do not create)[cite: 1].
* **Encryption:** Keep *AWS owned key* or default[cite: 1].
* **Deletion protection:** Temporarily set to **Off**[cite: 1].
* **Tags:** Can be skipped[cite: 1].

After reviewing all properties, click the **Create table** button at the bottom[cite: 1]. The system will initialize the table until its status switches to **Active**[cite: 1].

![DynamoDB Table in Active Status](dynamodb-table-active.png)