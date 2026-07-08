---
title : "Create Sample Room Item"
date : 2026-07-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

Now let's create a sample item to prove the table works.

1. **Open Explore table items**
   * Go to **DynamoDB** -> **Tables** -> `EnergyWasteData`.
   * Select **Explore table items**.

![EnergyWasteData table settings - Explore table items](/images/5-Workshop/5.4-dynamodb/pic6.png)

2. **Create the item in JSON view**
   * Click **Create item**.
   * If the interface has a button to switch views, select **JSON view**.
   * Paste this item:

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
```

![Edit item - JSON view](/images/5-Workshop/5.4-dynamodb/pic1.png)

3. **Verify the item was saved**
   * Click **Save**.
   * Run **Scan** to confirm the item appears in the results.

![Item saved successfully - Explore items result](/images/5-Workshop/5.4-dynamodb/pic7.png)
