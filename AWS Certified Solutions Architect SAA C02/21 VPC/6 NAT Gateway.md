# 6. NAT Gateway

- AWS managed NAT, higher bandwidth, better availability, no admin
- Pay by the hour for usage and bandwidth
- NAT is created in a specific AZ, uses an EIP
- Cannot be used by an instance in that subnet (only from other subnets)
- Requires an IGW (Private Subnet => NAT => IGW)
- 5 Gbps of bandwidth with automatic scaling up to 45 Gbps
- No security group to manage / required

![6%20NAT%20Gateway/Untitled.png](6%20NAT%20Gateway/Untitled.png)

---

# NAT Gateway with High Availability

- **NAT Gateway is resilient within a single-AZ**
- Must create **multiple NAT Gateway** in **multiple AZ** for fault-tolerance
- There is no cross AZ failover needed because if an AZ goes down it doesn't need NAT

![6%20NAT%20Gateway/Untitled%201.png](6%20NAT%20Gateway/Untitled%201.png)