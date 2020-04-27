# 1. Auto Scaling Alarm

- It is possible to scale an ASG based on CloudWatch alarms

![1%20Auto%20Scaling%20Alarm/Untitled.png](1%20Auto%20Scaling%20Alarm/Untitled.png)

- CloudWatch alarm is something that is going to be monitor few metrics

    When metrics go up → It will say "You should scale out!", Add instaces

    When the alarm goes back down, or there is another alarm saying it is too low → We can scale in

    → Basically, the ASG will scale based on the alarms

- An Alarm monitors a metric (such as Average CPU)
- **Metrics are computed for the overall ASG instances**
- Based on the alarm:
    - We can create scale-out policies (increase the number of instances)
    - We can create scale-in policies (decrease the number of instances)