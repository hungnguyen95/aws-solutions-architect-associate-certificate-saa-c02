# 3. AWS Config

- Helps with auditing and recording **compliance** of your AWS resources
- Helps record configurations and changes over time
- Possibility of storing the configuration data into S3 (analyzed by Athena)
- Questions that can be solved by AWS Config:
    - Is there unrestricted SSH access to my security groups?
    - Do my buckets have any public access?
    - How has my ALB configuration changed over time?
- You can receive alerts (SNS notifications) for any changes
- AWS Config is a per-region service
- Can be aggregated across regions and accounts

---

# AWS Config Resource

- View compliance of a resource over time

![3%20AWS%20Config/Untitled.png](3%20AWS%20Config/Untitled.png)

- View configuration of a resource over time

![3%20AWS%20Config/Untitled%201.png](3%20AWS%20Config/Untitled%201.png)

- View CloudTrail API calls if enabled

---

# AWS Config Rules

- Can use AWS managed config rules (over 75)
- Can make custom config rules (must be defined in AWS Lambda)
    - Evaluate if each EBS disk is of type gp2
    - Evaluate if each EC2 instance is t2.micro
- Rules can be evaluated / triggered
    - For each config change
    - And / or: at regular time intervals
    - Can trigger CloudWatch Events if the rule is non-compliant (and chain with Lambda)
- Rules can have auto remediations:
    - If a resource is not compliant, you can trigger an auto remediation
    - Ex: stop instances with non-approved tags
- **AWS Config Rules does not prevent actions from happening (no deny)**
- **Pricing**: no free tier, $2 per active rule per region per month