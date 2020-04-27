# 5. Cross zone balancing

- With Cross Zone Load Balancing: each load balancer instance distributes evenly across all registered instances in all AZ
- We have 3 AZs and 5 Instances. And we deployed a load balancer in three AZs.

    Cross-zone balancing: If we have it, that means our first instance in our first AZ for the load balancer, will be distributing traffic to all the EC2 Instances.

![5%20Cross%20zone%20balancing/Untitled.png](5%20Cross%20zone%20balancing/Untitled.png)

- And the second one and the third one will do this as well

![5%20Cross%20zone%20balancing/Untitled%201.png](5%20Cross%20zone%20balancing/Untitled%201.png)

- Otherwise, If we don't have cross-zone balancing enabled, each load balancer node distributes requests evenly across the registered instances in its Availability Zone only

![5%20Cross%20zone%20balancing/Untitled%202.png](5%20Cross%20zone%20balancing/Untitled%202.png)

- The first load balancer instance will be only redirecting to your EC2 Instances within your AZ1. Same for AZ2 and AZ3

---

- **Classic Load Balancer**
    - Disabled by default
    - No charges for inter AZ data if enabled
- **Application Load Balancer**
    - Always on (can’t be disabled)
    - No charges for inter AZ data
- **Network Load Balancer**
    - Disabled by default
    - You pay charges ($) for inter AZ data if enabled