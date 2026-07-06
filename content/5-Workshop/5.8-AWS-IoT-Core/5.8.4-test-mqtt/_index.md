---
title : "Test MQTT Message"
date : 2026-07-05 
weight : 4
chapter : false
pre : " <b> 5.8.4 </b> "
---

Now we will manually publish a message to test:

1. In AWS IoT Core, choose the left menu: **Test**[cite: 11].
2. Choose: **MQTT test client**[cite: 11].
3. **Step 2: Subscribe topic**[cite: 11]
   + Choose the tab: **Subscribe to a topic**[cite: 11].
   + In **Topic filter**, enter: `home/lab/telemetry`[cite: 11].
   + If there is a QoS section, choose: **QoS 0**[cite: 11].
   + Click: **Subscribe**[cite: 11].
   + On the left or bottom, a subscription should appear: `home/lab/telemetry`[cite: 11].

![Subscribe](/images/5-Workshop/5.8-AWS-IoT-Core/MQTT test client1.png)

4. **Step 3: Publish message**[cite: 11]
   + Choose the tab: **Publish to a topic**[cite: 11].
   + In **Topic name**, enter: `home/lab/telemetry`[cite: 11].
   + If there is QoS, choose: **0**[cite: 11].
   + If there is Retain message, keep: **Off**[cite: 11].
   + Delete the sample payload and paste[cite: 11]:

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

   + Click: **Publish**[cite: 11].

![Publish](/images/5-Workshop/5.8-AWS-IoT-Core/02-mqtt-test-message1.png)