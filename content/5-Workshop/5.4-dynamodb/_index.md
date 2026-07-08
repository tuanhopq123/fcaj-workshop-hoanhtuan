---
title: "5.4. Create DynamoDB Table"
date: 2026-07-01T17:00:00+07:00
draft: false
weight: 4
tags: ["aws", "dynamodb", "database"]
categories: ["Workshop"]
description: "Overview of creating a DynamoDB table to store room profiles and energy waste data for the project."
---

Amazon DynamoDB is used as the main data store for the project, holding room profiles and the energy waste data collected from sensors.

In this section, we will perform three main steps:

### 1. [Create DynamoDB Table](5.4.1-create-dynamodb/)
Instructions on how to access the DynamoDB console and start creating the `EnergyWasteData` table.

### 2. [Configure Table Details](5.4.2-configure-table/)
Step-by-step guidance to configure the partition key, sort key, and capacity mode for the table.

### 3. [Create Sample Room Item](5.4.3-create-sample-item/)
How to create a sample item in the table to verify that it works correctly.
