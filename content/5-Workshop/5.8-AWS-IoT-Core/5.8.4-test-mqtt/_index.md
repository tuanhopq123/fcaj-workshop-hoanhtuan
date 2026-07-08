---
title : "Test MQTT Message"
date : 2026-07-05 
weight : 4
chapter : false
pre : " <b> 5.8.4 </b> "
---

Now we will manually publish a message to test:

1. In AWS IoT Core, choose the left menu: **Test**.
2. Choose: **MQTT test client**.
3. **Step 2: Subscribe topic**
   + Choose the tab: **Subscribe to a topic**.
   + In **Topic filter**, enter: `home/lab/telemetry`.
   + If there is a QoS section, choose: **QoS 0**.
   + Click: **Subscribe**.
   + On the left or bottom, a subscription should appear: `home/lab/telemetry`.

![Subscribe](/images/5-Workshop/5.8-AWS-IoT-Core/MQTT test client1.png)

4. **Step 3: Publish message**
   + Choose the tab: **Publish to a topic**.
   + In **Topic name**, enter: `home/lab/telemetry`.
   + If there is QoS, choose: **0**.
   + If there is Retain message, keep: **Off**.
   + Delete the sample payload and paste:

    {
      "sensorId": "manual-iot-test-01",
      "roomId": "lab-01",
      "timestamp": "2026-07-03T03:00:00Z",
      "deviceId": "aircon-01",
      "deviceName": "Air Conditioner",
      "deviceStatus": "ON",
      "occupancy": false,
      "powerW": 200,
      "voltageV": 220,
      "currentA": 0.91,
      "energyKwh": 1.5
    }

   + Click: **Publish**.

![Publish](/images/5-Workshop/5.8-AWS-IoT-Core/02-mqtt-test-message1.png)