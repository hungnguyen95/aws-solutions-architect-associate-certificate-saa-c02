# 7. AWS WAF – Web Application Firewall

- Protects your web applications from common web exploits (Layer 7)
- Deploy on **Application Load Balancer, API Gateway, CloudFront**
- **WAF is not for DDoS protection**
- Define Web ACL (Web Access Control List):
    - Rules can include: **IP addresses**, HTTP headers, HTTP body, or URI strings
    - Protects from common attack - **SQL injection** and Cross-Site Scripting (XSS)
    - Size constraints, Geo match
    - Rate-based rules (to count occurrences of events)

---

# AWS Firewall Manager

- Manage rules in all accounts of an AWS Organization
- Common set of security rules
- WAF rules (Application Load Balancer, API Gateways, CloudFront)
- AWS Shield Advanced (ALB, CLB, Elastic IP, CloudFront)
- Security Groups for EC2 and ENI resources in VPC

![7%20AWS%20WAF%20Web%20Application%20Firewall/Untitled.png](7%20AWS%20WAF%20Web%20Application%20Firewall/Untitled.png)