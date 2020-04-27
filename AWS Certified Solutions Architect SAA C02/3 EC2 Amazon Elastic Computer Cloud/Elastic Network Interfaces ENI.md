# Elastic Network Interfaces (ENI)

- Logical component in a VPC that represents a **virtual network card**

![Elastic%20Network%20Interfaces%20ENI/Untitled.png](Elastic%20Network%20Interfaces%20ENI/Untitled.png)

- **For example**, we have an AZ and we have one EC2 Instance, and to it is attached on eth0, your primary ENI and this will provide your EC2 network connectivity. (for e.g: a private IP)
- The ENI can have the following attributes:
    - Primary private IPv4, one or more secondary IPv4

        ![Elastic%20Network%20Interfaces%20ENI/Untitled%201.png](Elastic%20Network%20Interfaces%20ENI/Untitled%201.png)

        →We can go to ENI settings and add one or more secondary IPv4 to ENI

    - We have one eth0, but we're welcomed to add a secondary ENI to EC2 (Eth1 in this example) and it will give you another private IPv4 → We can add multiple ENI to a EC2 Instance

    ![Elastic%20Network%20Interfaces%20ENI/Untitled%202.png](Elastic%20Network%20Interfaces%20ENI/Untitled%202.png)

    - Each ENI has One Elastic IP (IPv4) per private IPv4

    → One Elastic IP (IPv4) or One Public IPv4

    - One or more security groups attach to your ENI
    - A MAC address attach to ENI
- You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover
- Bound to a specific availability zone (AZ)

![Elastic%20Network%20Interfaces%20ENI/Untitled%203.png](Elastic%20Network%20Interfaces%20ENI/Untitled%203.png)

- Here's another instance and it has another ENI attached to it. And we can move the Eth1 from the first EC2 Instance to the second EC2 Instance to move private IP → the private will change from the first to the second Instance. It's very helpful for failovers

![Elastic%20Network%20Interfaces%20ENI/Untitled%204.png](Elastic%20Network%20Interfaces%20ENI/Untitled%204.png)

→ Eth0 can not be detached