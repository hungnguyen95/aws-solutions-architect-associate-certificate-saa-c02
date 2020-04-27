# 16. AWS PrivateLink

# Exposing services in your VPC to other VPC

- Option 1: make it public
    - Goes through the public www
    - Tough to manage access

![16%20AWS%20PrivateLink/Untitled.png](16%20AWS%20PrivateLink/Untitled.png)

- Option 2: VPC peering
    - Must create many peering relations
    - Opens the **whole** network

![16%20AWS%20PrivateLink/Untitled%201.png](16%20AWS%20PrivateLink/Untitled%201.png)

---

# AWS Private Link (VPC Endpoint Services)

- Most secure & scalable way to expose a service to 1000s of VPC (own or other accounts)
- Does not require VPC peering, internet gateway, NAT, route tables, ...
- Requires a network load balancer (Service VPC) and ENI (Customer VPC)
- If the NLB is in multiple AZ, and the ENI in multiple AZ, the solution is fault tolerant!

![16%20AWS%20PrivateLink/Untitled%202.png](16%20AWS%20PrivateLink/Untitled%202.png)