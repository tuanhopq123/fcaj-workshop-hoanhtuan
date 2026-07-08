---
title: "5.5. Set Up Amazon SNS Alerts"
date: 2026-07-01T17:30:00+07:00
draft: false
weight: 5
tags: ["aws", "sns", "notifications"]
categories: ["Workshop"]
description: "Overview of setting up Amazon SNS to send email alerts when energy waste is detected."
---

Amazon SNS (Simple Notification Service) is used to send email alerts whenever the system detects energy waste, such as a device left on in an unoccupied room.

In this section, we will perform seven main steps:

### 1. [Open Amazon SNS](5.5.1-open-sns/)
Instructions on how to access the Amazon SNS console and start creating a topic.

### 2. [Create an SNS Topic](5.5.2-create-topic/)
Step-by-step guidance to create the `energy-waste-alert-topic` topic.

### 3. [Create Email Subscription](5.5.3-create-email-subscription/)
How to subscribe an email address to the topic so it can receive alerts.

### 4. [Confirm SNS Subscription Email](5.5.4-confirm-subscription-email/)
How to find and confirm the subscription email sent by AWS.

### 5. [Check Subscription Status](5.5.5-check-subscription-status/)
How to verify that the subscription status is **Confirmed**.

### 6. [Test Sending an Alert Email](5.5.6-test-publish-message/)
How to publish a test message to the topic to simulate an energy waste alert.

### 7. [Check the Received Email](5.5.7-check-received-email/)
How to verify that the test alert email was received successfully.
