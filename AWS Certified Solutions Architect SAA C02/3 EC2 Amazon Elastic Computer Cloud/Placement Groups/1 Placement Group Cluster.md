# 1. Placement Group Cluster

![1%20Placement%20Group%20Cluster/Untitled.png](1%20Placement%20Group%20Cluster/Untitled.png)

- All our EC2 instances are on the same rack, which means same hardware and it's in the same AZ
- Pros: Great network (10 Gbps bandwidth between instances)
- Cons: If the rack fails, all instances fails at the same time
- Use case:
    - Big Data job that needs to complete fast
    - Application that needs extremely low latency and high network throughput