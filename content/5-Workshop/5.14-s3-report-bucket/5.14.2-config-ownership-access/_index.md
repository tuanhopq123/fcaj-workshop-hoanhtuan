---
title : "Configure Ownership and Public Access"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.14.2. </b> "
---

#### Object Ownership

Under the **Object Ownership** section, keep the default setting:
- **ACLs disabled (Bucket owner enforced)**

*Note: Do not enable ACLs. With "Bucket owner enforced", ACLs are disabled and access is managed purely through IAM policies or bucket policies. This is the default and recommended setting for new general purpose buckets.*

#### Block Public Access

Under the **Block Public Access settings for this bucket** section, ensure the following is enabled:
- **Block all public access**

*Note: All four underlying options must remain checked. Do not uncheck them or confirm granting public access. AWS recommends keeping Block Public Access enabled for buckets that do not require public access; this setting overrides any bucket policies or ACLs that attempt to grant public access.*

#### Bucket Versioning

For **Bucket Versioning**, select: **Disable**

*Note: The project currently does not need to store multiple versions of the same report file. Each report will have a unique object key based on its date, so versioning is unnecessary at this stage.*

#### Tags

- You can leave this blank.
- Optionally, you can add a tag for easier management:
  - **Key**: `Project`
  - **Value**: `EnergyWasteMonitoring`