# 5. Auto Scaling Group

- In real-life, the load on your websites and application can change
- In the cloud, you can create and get rid of servers very quickly
- The goal of an Auto Scaling Group (ASG) is to:
    - Scale out (add EC2 instances) to match an increased load
    - Scale in (remove EC2 instances) to match a decreased load
    - Ensure we have a minimum and a maximum number of machines running
    - Automatically Register new instances to a load balancer
- The minimum size (for example 1 here) is a number of EC2 instances you'll have for sure running into this Auto Scaling Group

![5%20Auto%20Scaling%20Group/Untitled.png](5%20Auto%20Scaling%20Group/Untitled.png)

- The actual size, or desired capacity parameter is the number of EC2 instances running at the previous moment, in the current moment in your ASG

![5%20Auto%20Scaling%20Group/Untitled%201.png](5%20Auto%20Scaling%20Group/Untitled%201.png)

- And then you have the maximum size which is how many instances can be added for scale out if needed when the load goes up

![5%20Auto%20Scaling%20Group/Untitled%202.png](5%20Auto%20Scaling%20Group/Untitled%202.png)

---

Here is our load balancer and web traffic goes straight through it and we have an auto scaling group at the bottom. Basically the load balancer will know directly how to connect to these ASG instances

![5%20Auto%20Scaling%20Group/Untitled%203.png](5%20Auto%20Scaling%20Group/Untitled%203.png)

But if our Auto Scaling Group scales out, so if we add EC2 instances, then the load balancers will also register these targets, obviously perform health checks, and directly reach traffic back to them.

![5%20Auto%20Scaling%20Group/Untitled%204.png](5%20Auto%20Scaling%20Group/Untitled%204.png)

→ Load balancer and auto scaling groups really work hand in hand in AWS

---

# ASGs have the following attributes

- A launch configuration
    - AMI + Instance Type
    - EC2 User Data
    - EBS Volumes
    - Security Groups
    - SSH Key Pair
- Min Size / Max Size / Initial Capacity
- Network + Subnets Information
- Load Balancer Information
- Scaling Policies

[1. Auto Scaling Alarm](5%20Auto%20Scaling%20Group/1%20Auto%20Scaling%20Alarm.md)

[2. Auto Scaling New Rules](5%20Auto%20Scaling%20Group/2%20Auto%20Scaling%20New%20Rules.md)

[3. Auto Scaling custom metric](5%20Auto%20Scaling%20Group/3%20Auto%20Scaling%20custom%20metric.md)

[4. ASG Brain Dump](5%20Auto%20Scaling%20Group/4%20ASG%20Brain%20Dump.md)

[5. Scaling Policies](5%20Auto%20Scaling%20Group/5%20Scaling%20Policies.md)

[6. Scaling Cooldown](5%20Auto%20Scaling%20Group/6%20Scaling%20Cooldown.md)

[7. ASG for Solution Architect](5%20Auto%20Scaling%20Group/7%20ASG%20for%20Solution%20Architect.md)