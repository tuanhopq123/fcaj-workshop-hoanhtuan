---
title : "Gỡ AWS WAF khỏi Amplify"
date : 2026-07-05 
weight : 2
chapter : false
pre : " <b> 5.18.2 </b> "
---

Không thể xóa Web ACL khi nó vẫn đang liên kết với ứng dụng Amplify. Phải gỡ liên kết trước rồi mới xóa Web ACL.

1. **Mở ứng dụng Amplify**
   * Tìm và mở **AWS Amplify**.
   * Chọn ứng dụng: `energy-waste-dashboard`.
   * Mở **Hosting** -> **Firewall**.

2. **Gỡ Web ACL**
   * Tìm Web ACL đang liên kết, chọn **Actions** -> **Disassociate firewall**.
   * Nhập xác nhận và chờ trạng thái liên kết được gỡ bỏ.

3. **Xóa Web ACL**
   * Tìm và mở **AWS WAF & Shield**.
   * Đổi Region thành **Global (CloudFront)** và chọn **Web ACLs**.
   * Chọn Web ACL vừa gỡ, bấm **Delete** và xác nhận.

![Gỡ WAF 1](/images/5-Workshop/5.18-CleanUp/Xoa-Web-ACL.png)
![Gỡ WAF 2](/images/5-Workshop/5.18-CleanUp/Xoa-Web-ACL2.png)