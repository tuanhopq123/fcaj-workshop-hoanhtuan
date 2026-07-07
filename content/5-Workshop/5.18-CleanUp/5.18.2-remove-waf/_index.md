---
title : "Remove AWS WAF from Amplify"
date : 2026-07-05 
weight : 2
chapter : false
pre : " <b> 5.18.2 </b> "
---

You cannot delete a Web ACL while it is associated with an Amplify app. You must disassociate it first.

1. **Open Amplify App**
   * Search for and open **AWS Amplify**.
   * Choose the app: `energy-waste-dashboard`.
   * Navigate to **Hosting** -> **Firewall**.

2. **Disassociate Web ACL**
   * Find the associated Web ACL. Click **Actions** -> **Disassociate firewall**.
   * Confirm and wait for the association to be removed.

3. **Delete Web ACL**
   * Search for and open **AWS WAF & Shield**.
   * Set the Region to **Global (CloudFront)** and select **Web ACLs**.
   * Select your Web ACL, click **Delete**, and confirm.

![Remove WAF 1](/images/5-Workshop/5.18-CleanUp/Xoa-Web-ACL.png)
![Remove WAF 2](/images/5-Workshop/5.18-CleanUp/Xoa-Web-ACL2.png)