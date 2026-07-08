---
title : "Attach Lambda Action"
date : 2026-07-05 
weight : 3
chapter : false
pre : " <b> 5.8.3 </b> "
---

1. The next page is usually named: **Attach rule actions**.
2. In the **Rule actions** section, click: **Add action** *(If the interface already has an action selection box, no need to click Add action)*.
3. For **Action type** or **Choose an action**, choose: **Lambda** *(The name in the interface might be displayed as `Lambda` or `Send a message to a Lambda function`)*.
4. For **Lambda function**, choose: `energy-waste-detector`.
   + *Do not choose `energy-virtual-sensor`*.
5. If there is a **Version or alias** section, leave the default: `$LATEST` (or leave blank if the Console does not require it).
6. Do not create an IAM execution role for this action.
7. Click: **Next**.
8. Click: **Create**.

![Review](/images/5-Workshop/5.8-AWS-IoT-Core/rules2.png)

Creation success message:

![Success](/images/5-Workshop/5.8-AWS-IoT-Core/rules3.png)

#### Check Lambda permissions added automatically by AWS IoT

1. Open a new AWS Console tab.
2. Navigate to: **Lambda → Functions → energy-waste-detector**.
3. Choose: **Configuration → Permissions**.
4. Find: **Resource-based policy statements**. Expand the policy if needed.
5. You should see a statement with content similar to:
   + **Principal:** `iot.amazonaws.com`
   + **Action:** `lambda:InvokeFunction`
6. The Source ARN must be related to the rule: `arn:aws:iot:ap-southeast-1:347685737655:rule/iot_rule_energy_telemetry_to_waste_detector`.

{{% notice note %}}
This is not an inline policy of the execution role. This is the resource-based policy of Lambda.
{{% /notice %}}

![Permissions](/images/5-Workshop/5.8-AWS-IoT-Core/01-iot-rule-details.png)