---
title : "Kiểm tra các rule bảo vệ"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.17.3. </b> "
---

#### Thực hiện

1. Trên thanh tab phía trên, bấm: **Rules**.
2. Amplify đã tự động tạo 3 **AWS Managed Rule Groups**:
   - **Priority 0**: `AWS-AWSManagedRulesAmazonIpReputationList`
   - **Priority 1**: `AWS-AWSManagedRulesCommonRuleSet`
   - **Priority 2**: `AWS-AWSManagedRulesKnownBadInputsRuleSet`

![Kiểm tra các rule bảo vệ](/images/5-Workshop/5.17-cloudfront-waf/5.17.3-waf-rules.png)

#### Kết quả xác thực

Điều này chứng minh request truy cập trang chủ dashboard đã đi theo luồng:
**Người dùng** -> **Hệ thống phân phối của Amplify** -> **AWS WAF kiểm tra** -> **ALLOW** -> **Dashboard được hiển thị**.

![Kết quả WAF request thành công](/images/5-Workshop/5.17-cloudfront-waf/5.17.3-waf-success.png)