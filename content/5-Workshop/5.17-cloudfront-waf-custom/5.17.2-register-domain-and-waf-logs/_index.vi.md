---
title : "Register Domain and Verify WAF Logs"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.17.2. </b> "
---

#### A. Search and Register Domain

1. Open **Amazon Route 53**.
2. Select: **Domains** -> **Registered domains**.
3. Click **Register domains**.
4. In the search box, enter exactly: `energywastelab.site` (or your chosen domain).
5. Click **Search**.

![Search Domain](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-search-domain.png)

6. Select `energywastelab.com` ($15/year).
7. Click **Proceed to checkout**.

![Select Domain](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-select-domain.png)

*To avoid automatic renewal charges next year:*
8. Keep **Duration** at `1 year`.
9. **Uncheck**: **Auto-renew - On**.
10. Click **Next**.

![Configure Renewal](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-disable-autorenew.png)

11. Enter **Contact Information** and click **Next**.

![Contact Information](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-contact-info.png)

12. Click **Next** to confirm registration.

![Confirm Registration](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-confirm-registration.png)

*Note: If registration fails, proceed to verify WAF logs.*

#### B. Verify AWS WAF Logs

1. Return to **AWS Amplify** -> `energy-waste-dashboard`.
2. Go to: **Hosting** -> **Firewall**.
3. Ensure status is: **Web Application Firewall — Enabled**.
4. Click: **View WAF logs**.

![View WAF Logs](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-view-waf-logs.png)

5. On the top tab, click: **Associated AWS resources**.
6. Verify the Web ACL is protecting:
   - **Name**: `energy-waste-dashboard`
   - **Resource type**: `Amplify Application`
   - **Associated AWS resources**: `1`

![Associated Resources](/images/5-Workshop/5.17-cloudfront-waf/5.17.2-associated-resources.png)