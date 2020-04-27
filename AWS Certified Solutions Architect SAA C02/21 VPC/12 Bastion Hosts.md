# 12. Bastion Hosts

- We can use a Bastion Host to SSH into our private instances
- The bastion is in the public subnet which is then connected to all other private subnets
- **Bastion Host security group must be tightened**
- Exam Tip: Make sure the bastion host only has port 22 traffic from the IP you need, not from the security groups of your other instances

![12%20Bastion%20Hosts/Untitled.png](12%20Bastion%20Hosts/Untitled.png)