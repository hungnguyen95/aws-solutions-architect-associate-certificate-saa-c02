# 3. Subnet Overview

# Adding Subnets

![3%20Subnet%20Overview/Untitled.png](3%20Subnet%20Overview/Untitled.png)

- Each AZ → Create different subnets
    - A public subnet
    - A private subnet

    → Multi AZs for high availability

---

# Subnets - IPv4

- AWS reserves 5 IPs address (first 4 and last 1 IP address) in each Subnet
- These 5 IPs are not available for use and cannot be assigned to an instance
- Ex, if CIDR block 10.0.0.0/24, reserved IP are:
    - 10.0.0.0: Network address
    - 10.0.0.1: Reserved by AWS for the VPC router
    - 10.0.0.2: Reserved by AWS for mapping to Amazon-provided DNS
    - 10.0.0.3: Reserved by AWS for future use
    - 10.0.0.255: Network broadcast address. AWS does not support broadcast in a VPC,

    therefore the address is reserved

- Exam Tip:
    - If you need 29 IP addresses for EC2 instances, you can’t choose a Subnet of size /27 (32 IP)
    - You need at least 64 IP, Subnet size /26 (64-5 = 59 > 29, but 32-5 = 27 < 29)