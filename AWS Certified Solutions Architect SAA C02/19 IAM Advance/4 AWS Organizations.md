# 4. AWS Organizations

- Global service
- Allows to manage multiple AWS accounts
- The main account is the master account – you can’t change it
- Other accounts are member accounts
- Member accounts can only be part of one organization
- Consolidated Billing across all accounts - single payment method
- Pricing benefits from aggregated usage (volume discount for EC2, S3…)
- API is available to automate AWS account creation

---

# Multi Account Strategies

- Create accounts per **department**, per **cost center**, per **dev** / **test** /**prod**, based on **regulatory restrictions** (using SCP), for **better resource isolation** (ex: VPC), to have **separate per-account service limits**, isolated account for **logging**
- Multi Account vs One Account Multi VPC

    ⇒ Multi Account: many accounts used in 1 VPC

    ⇒ 1 Account Multi VPC: 1 account access many resources, access to multiple VPC

- Use tagging standards for billing purposes
- Enable CloudTrail on all accounts, send logs to central S3 account
- Send CloudWatch Logs to central logging account
- Establish Cross Account Roles for Admin purposes

---

# Organizational Units (OU) - Examples

![4%20AWS%20Organizations/Untitled.png](4%20AWS%20Organizations/Untitled.png)

---

# AWS Organization

![4%20AWS%20Organizations/Untitled%201.png](4%20AWS%20Organizations/Untitled%201.png)

---

# Service Control Policies (SCP)

- Whitelist or blacklist IAM actions
- Applied at the **Root**, **OU** or **Account level**
- SCP is applied to all the **Users and Roles** of the Account, including Root
- The SCP does not affect service-linked roles
    - Service-linked roles enable other AWS services to integrate with AWS Organizations and can't be restricted by SCPs.
- SCP must have an explicit Allow (does not allow anything by default)
- Use cases:
    - Restrict access to certain services (for example: can’t use EMR)
    - Enforce PCI compliance by explicitly disabling services

---

# SCP Hierarchy

![4%20AWS%20Organizations/Untitled%202.png](4%20AWS%20Organizations/Untitled%202.png)

---

# SCP Examples Blacklist and Whitelist strategies

![4%20AWS%20Organizations/Untitled%203.png](4%20AWS%20Organizations/Untitled%203.png)

---

# AWS Organization – Moving Accounts

**To migrate accounts from one organization to another:**

1. Remove the member account from the old organization
2. Send an invite to the new organization
3. Accept the invite to the new organization from the member account

**If you want the master account of the old organization to also join the new organization, do the following:**

1. Remove the member accounts from the organizations using procedure above (migrate from old to new org)
2. Delete the old organization
3. Repeat the process above to invite the old master account to the new org

![4%20AWS%20Organizations/Untitled%204.png](4%20AWS%20Organizations/Untitled%204.png)