# 5. Scaling Policies

- **Target Tracking Scaling**
    - Most simple and easy to set-up
    - Example: I want the average ASG CPU to stay at around 40%

        That means if you're over that CPU, you will provision more instances to serve your ASG, and if you're under that CPU, it will start doing scaling in → stay around average 40% CPU

- **Simple / Step Scaling**

    You would set up something called a CloudWatch alarm

    - When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units
    - When a CloudWatch alarm is triggered (example CPU < 30%), then remove 1
- **Scheduled Actions**
    - Anticipate a scaling based on known usage patterns
    - For e.g: you know that at 5p.m on Fridays, you need to increase the min capacity to 10 instances because you know that you will need