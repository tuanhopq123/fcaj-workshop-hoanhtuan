---
title : "Verify IoT Flow"
date : 2026-07-05 
weight : 5
chapter : false
pre : " <b> 5.8.5 </b> "
---

AWS IoT calls Lambda asynchronously, so after publishing, wait a few seconds before checking the results[cite: 11].

#### A. Check DynamoDB

1. Open a new AWS Console tab[cite: 11].
2. Search for: **DynamoDB**[cite: 11].
3. Choose: **Tables**[cite: 11].
4. Select the table: `EnergyWasteData`[cite: 11].
5. Click: **Explore table items**[cite: 11].

![DynamoDB Table](/images/5-Workshop/5.8-AWS-IoT-Core/DynamoDB.png)

![DynamoDB Items](/images/5-Workshop/5.8-AWS-IoT-Core/03-dynamodb-telemetry-alert.png)

#### B. Check SNS Email

1. Open the email registered with SNS[cite: 11].
2. You should receive an email containing the JSON alert data from AWS Energy Waste Alert[cite: 11].

![SNS Email](/images/5-Workshop/5.8-AWS-IoT-Core/04-email-alert-from-iot-rule.png)