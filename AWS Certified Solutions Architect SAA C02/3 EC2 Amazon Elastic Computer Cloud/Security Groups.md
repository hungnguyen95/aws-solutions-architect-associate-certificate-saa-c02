# Security Groups

- Security Groups are the fundamental of network security in AWS
- They control how traffic is allowed into or out of our EC2 Machines.
- It is the most fundamental skill to learn to troubleshoot networking issues

![Security%20Groups/Untitled.png](Security%20Groups/Untitled.png)

- Security groups are acting as a “firewall” on EC2 instances
- They regulate:
    - Access to Port
    - Authorized IP Ranges - IPv4 and IPv6
    - Control of inbound network (from other to the instance)
    - Control of outbound network (from the instance to other)

![Security%20Groups/Untitled%201.png](Security%20Groups/Untitled%201.png)

- Security Group can restrict IP ranges, ports, ... If you were authorized by security groups, you can access it. But if you weren't you couldn't access to it.

![Security%20Groups/Untitled%202.png](Security%20Groups/Untitled%202.png)

- The relationship between Security Groups and EC2 is many-to-many relationship. One Security Groups an be attached to multiple instances (EC2) and vice versa.
- Security Group locked down to a region / VPC combination
- Does live “outside” the EC2 – if traffic is blocked the EC2 instance won’t see it
- It’s good to maintain one separate security group for SSH access
- If your application is not accessible (time out), then it’s a security group issue
- If your application gives a “connection refused“ error, then it’s an application error or it’s not launched
- All inbound traffic is blocked by default
- All outbound traffic is authorized by default

[Referencing other security groups ](Security%20Groups/Referencing%20other%20security%20groups.md)