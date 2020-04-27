# 2. Placement Group Spread

![2%20Placement%20Group%20Spread/Untitled.png](2%20Placement%20Group%20Spread/Untitled.png)

- Minimize the failure risks.
- All the EC2 instances are going to be located on different hardware
- As image above, we have 3 AZs and we have 6 EC2 and each EC2 instance is on a different hardware.
- Pros:
    - Can span across Availability Zones (AZ)
    - Reduced risk is simultaneous failure

    → If my Hardware 1 fail, I'm pretty sure that Hardware 2 will not fail. And so we've separated the risk of my two instances in us-east-1a to fail at the same time.

    - EC2 Instances are on different physical hardware
- Cons:
    - Limited to 7 instances per AZ per placement group
- Use cases:
    - Application that needs to maximize high availability
    - Critical Applications where each instance must be isolated from failure from each other