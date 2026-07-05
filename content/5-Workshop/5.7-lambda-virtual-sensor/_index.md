---
title: "5.7. Create Lambda Virtual Sensor"
date: 2026-07-05
weight: 7
chapter: true
---

# 5.7. Create Lambda Virtual Sensor

The Lambda Virtual Sensor is responsible for simulating real-world power consumption data from laboratory equipment and publishing these telemetry payloads directly to AWS IoT Core.

In this section, you will go through the following steps to build and test the virtual sensor:
1. **Create a Lambda Function**: Initialize the function using the Python runtime.
2. **Configure Environment Variables**: Set dynamic variables for flexibility.
3. **Grant IAM Permissions**: Allow the function to publish data to AWS IoT Core.
4. **Deploy the Simulation Source Code**: Implement the Python simulation script.
5. **Create a Test Event**: Define custom configurations for manual execution.
6. **Execute Test and Verify Results**: Validate the system behavior and output logs.