---
title: "5.5.1 Create SNS Topic"
weight: 1
description: "Configure Standard Topic classification with customized Name and Display Name attributes."
---

# 5.5.1 Create a New SNS Topic

Proceed to initialize the required identity parameters for your messaging hub using the configuration values detailed below[cite: 2]:

### Specification Criteria:

* **Type:** Select the **Standard** option[cite: 2].
* **Name:** `energy-waste-alert-topic`[cite: 2]
* **Display name - optional:** `EnergyWasteAlert`[cite: 2]

> 💡 **Architecture Insight:** Unlike FIFO profiles which guarantee strict ordering, the **Standard** delivery type yields maximum throughput performance while supporting an expansive set of endpoint protocols including Lambda, Email, and SQS, matching our dynamic energy monitoring requirements[cite: 2].

![SNS Topic Attribute Setup](sns-topic-config.png)

Once you complete entering the parameters above, scroll to the bottom of the section and click the **Create topic** button[cite: 2].

The console interface will refresh to reveal a green banner reading: *"Topic energy-waste-alert-topic created successfully."*[cite: 2], indicating the asset is ready for target registration[cite: 2].

![Confirming Successful Topic Creation](sns-topic-created.png)