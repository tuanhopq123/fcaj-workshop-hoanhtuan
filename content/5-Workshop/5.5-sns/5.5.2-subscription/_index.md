---
title: "5.5.2 Register & Confirm Email Subscription"
weight: 2
description: "Bind a targeted notification email endpoint to the SNS Topic and execute subscription verification actions."
---

# 5.5.2 Build and Validate Email Subscription

With the parent topic established, we must couple a communication endpoint to process outbound notification payloads[cite: 2]. This laboratory relies on the **Email** transfer mechanism[cite: 2].

### Step 1: Initiate Subscription in the Console

1. On the detail sheet for `energy-waste-alert-topic`, navigate down to the **Subscriptions** pane[cite: 2].
2. Click the **Create subscription** button[cite: 2].
3. Populate the field variables using the properties below[cite: 2]:
   * **Topic ARN:** Leave untouched (it references the active topic context automatically)[cite: 2].
   * **Protocol:** Click the option dropdown list and choose **Email**[cite: 2].
   * **Endpoint:** Provide your personal, active email address where alert items should be redirected[cite: 2].

![Configuring Email Subscription Settings](sns-create-email-subscription.png)

4. Click the **Create subscription** action button[cite: 2].

---

### Step 2: Approve the Subscription Request

AWS messaging workflows invoke a safety constraint requiring owner validation before distributing data[cite: 2].

1. Access the webmail inbox corresponding to the target endpoint configured previously[cite: 2].
2. Look for an automated delivery item arriving from **AWS Notifications**[cite: 2].
3. Expand the mail message view and click the embedded **Confirm subscription** link text[cite: 2].

Your internet browser will open a secondary workspace pane rendering a successful **Subscription confirmed!** block alongside the unique subscription identity string[cite: 2].

![Browser Displaying Subscription Confirmed](sns-email-confirmed-browser.png)

---

### Step 3: Audit State Verification on AWS Console

1. Return to the **AWS Console** terminal layout under `SNS` ➔ `Topics` ➔ `energy-waste-alert-topic`[cite: 2].
2. Examine the records pool within the **Subscriptions** layout block (Click the refresh reload option if mandatory)[cite: 2].
3. Assure that the data column attribute value transitions from *Pending confirmation* to a green label: **Confirmed**[cite: 2].

![Confirming Subscription Status Validation](sns-subscription-confirmed.png)