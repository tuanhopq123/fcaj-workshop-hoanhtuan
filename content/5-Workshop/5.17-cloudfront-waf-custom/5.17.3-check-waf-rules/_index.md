---
title : "Check WAF Protection Rules"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.17.3. </b> "
---

#### Execution Steps

1. On the top navigation bar, click the **Rules** tab.
2. Amplify will have automatically created three **AWS Managed Rule Groups**:
   - **Priority 0**: `AWS-AWSManagedRulesAmazonIpReputationList`
   - **Priority 1**: `AWS-AWSManagedRulesCommonRuleSet`
   - **Priority 2**: `AWS-AWSManagedRulesKnownBadInputsRuleSet`

![Check WAF Rule Groups](/images/5-Workshop/5.17-cloudfront-waf/5.17.3-waf-rules.png)

#### Result Verification

This confirms that any access request to the dashboard homepage follows this flow:
**User** -> **Amplify Distribution** -> **AWS WAF Inspection** -> **ALLOW** -> **Dashboard Displayed**.

![WAF Request Success](/images/5-Workshop/5.17-cloudfront-waf/5.17.3-waf-success.png)