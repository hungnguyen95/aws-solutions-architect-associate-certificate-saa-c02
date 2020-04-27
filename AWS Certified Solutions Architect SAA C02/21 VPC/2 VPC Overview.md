# 2. VPC Overview

- All new accounts have a default VPC
- New instances are launched into default VPC if no subnet is specified
- Default VPC have internet connectivity and all instances have public IP
- We also get a public and a private DNS name

---

# VPC in AWS – IPv4

- VPC = Virtual Private Cloud
- You can have multiple VPCs in a region (max 5 per region – soft limit)
- Max CIDR per VPC is 5. For each CIDR:
    - Min size is /28 = 16 IP Addresses
    - Max size is /16 = 65536 IP Addresses
- Because VPC is private, only the Private IP ranges are allowed:
    - 10.0.0.0 – 10.255.255.255 (10.0.0.0/8)
    - 172.16.0.0 – 172.31.255.255 (172.16.0.0/12)
    - 192.168.0.0 – 192.168.255.255 (192.168.0.0/16)
- **Your VPC CIDR should not overlap with your other networks (ex: corporate)**

---

# State of Hands On

![2%20VPC%20Overview/Untitled.png](2%20VPC%20Overview/Untitled.png)