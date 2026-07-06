---
title: "5.4.2 Create Sample Data (Room Item)"
weight: 2
description: "Insert a sample room record using JSON format to verify that the table works properly."
---

# 5.4.2 Create Sample Room Item

Now, let's create a sample item to verify that our newly created table is working properly.

### Step-by-step Instructions:

1. Navigate to: **DynamoDB** ➔ **Tables** ➔ select the `EnergyWasteData` table.
2. Click the **Explore table items** button in the top right corner.

![Accessing Explore Table Items Interface](/images/5-Workshop/5.4-dynamodb/11.png)

3. Click the **Create item** button[cite: 1].
4. In the Attributes section, switch the view mode toggle to **JSON view**[cite: 1].
5. Copy and paste the following JSON block into the editor[cite: 1]:

```json
{
  "PK": {
    "S": "ROOM#lab-01"
  },
  "SK": {
    "S": "PROFILE"
  },
  "entityType": {
    "S": "Room"
  },
  "roomId": {
    "S": "lab-01"
  },
  "roomName": {
    "S": "Smart Home Lab"
  },
  "powerThresholdW": {
    "N": "120"
  },
  "createdBy": {
    "S": "manual-console"
  }
}