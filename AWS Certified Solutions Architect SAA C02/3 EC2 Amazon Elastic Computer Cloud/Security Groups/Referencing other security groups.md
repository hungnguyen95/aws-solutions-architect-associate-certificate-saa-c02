# Referencing other security groups

Referencing other security groups Diagram

- You can define Security Groups reference to others Security Group.

    ![Referencing%20other%20security%20groups/Untitled.png](Referencing%20other%20security%20groups/Untitled.png)

    - In diagram above, you define that Security Group 1's Inbound will authorize all instances is attached by Security Group 1 and Security Group 2
    - Any instance is not attached by SG1 or SG2 will not be able to connect to this instance.

→ This pattern is most common when you combine many instances when you use ELB (Elastic Load Balancer)