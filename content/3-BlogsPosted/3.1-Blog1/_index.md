---
title: "Blog 1"
date: 2026-07-05
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# SUBDOMAIN TAKEOVER: A HIDDEN CLOUD SECURITY RISK

Today, I want to summarize and share a security risk that isn't new but is extremely easy to encounter when managing cloud infrastructure: **Subdomain Takeover**.

When deploying projects, we often create many resources (S3 Buckets, CloudFront, Elastic Beanstalk...) and point DNS records (like Route 53) to these resources. However, when a project ends, many people have the habit of only cleaning up resources to save costs while forgetting to delete the associated DNS records. This negligence unintentionally creates a fatal vulnerability for hackers to exploit.

![Normal Architecture](/images/3-blog/3.1-image1.png)

### The Attack Mechanism (Dangling DNS)

This process is incredibly simple but leaves severe consequences for brand reputation:

1. **Orphaned record:** A CNAME record in the DNS system (e.g., `promo.company.com`) points to an S3 bucket or Beanstalk environment (`promo-campaign.s3.amazonaws.com`).

![Route 53 Routing](/images/3-blog/3.1-image2.png)

2. **Deleting resource but keeping DNS:** The administrator deletes the `promo-campaign` bucket when the campaign ends but forgets to delete the CNAME record. At this point, `promo.company.com` is pointing to nowhere (Dangling DNS).

![Deleted Resource](/images/3-blog/3.1-image3.png)

3. **Attacker claims it:** Hackers continuously scan subdomains. When they detect a record pointing to a non-existent AWS resource, they immediately log into their AWS account and provision a new resource (e.g., an S3 bucket) with the exact name you deleted (`promo-campaign`).
4. **Takeover complete:** Now, when customers access `promo.company.com`, they will be directed to content entirely controlled by the hacker (phishing login pages, malware distribution, or bypassing CORS to steal cookies).

![Subdomain Takeover Complete](/images/3-blog/3.1-image4.png)

### Best Practices for Prevention

Instead of relying on human memory, AWS recommends automated and systematic approaches:

* **Lifecycle Management:** The golden rule in operations is to always delete DNS records (Route 53) before or at the same time as deleting or releasing the destination resources (S3, CloudFront, ELB, EC2 Elastic IP). Never leave DNS "hanging".
* **Use Alias Records instead of CNAMEs:** On AWS Route 53, prioritize using Alias Records to point internally between AWS services. Although Alias records do not 100% prevent Subdomain Takeover, they are more tightly managed and deeply integrated with the lifecycle of AWS resources compared to traditional CNAMEs.
* **Leverage AWS Security Updates:** AWS has continuously released under-the-hood protection mechanisms. For example, with CloudFront today, it is very difficult for an attacker to hijack a cross-account domain because CloudFront requires a valid TLS/SSL certificate or passing Domain Ownership Verification.
* **Automated Monitoring:** Set up rules in AWS Config or catch events via Amazon EventBridge to immediately alert if a Route 53 record is found pointing to a resource that no longer exists in the account.

![Automated Monitoring Architecture](/images/3-blog/3.1-image5.png)

### Conclusion and Recommendations

Subdomain Takeover is clear proof that misconfigurations can cause devastating consequences on par with high-tech attacks. Cloud security is not just about building firewalls to prevent external intrusions, but also about tight and clean Resource Lifecycle management from the inside.

**Recommendation:** For systems with hundreds of subdomains, DevOps/SecOps should proactively write automated scripts (using Python/Boto3) to run periodically via AWS Lambda. This script will scan the entire Hosted Zone in Route 53 and cross-reference it with the list of currently running resources. If an "orphaned" DNS is detected, the system can automatically send an alert via Slack/Telegram or automatically remove that record to instantly eliminate the risk.

---
**Sources:**
*   [AWS Study Group VN | Subdomain Takeover Chiếm quyền điều khiển tên miền phụ](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2202705877161039)
*   [Threat tactic spotlight: Subdomain takeover | AWS Security Blog](https://aws.amazon.com/blogs/security/threat-tactic-spotlight-subdomain-takeover/)