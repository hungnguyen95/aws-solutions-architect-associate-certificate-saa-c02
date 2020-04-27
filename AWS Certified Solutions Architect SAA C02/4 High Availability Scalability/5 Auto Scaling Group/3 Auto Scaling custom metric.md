# 3. Auto Scaling custom metric

- We can auto scale based on a custom metric (ex: number of connected users)

1. Send custom metric from application on EC2 to CloudWatch (PutMetric API)

2. Create CloudWatch alarm to react to low / high values

3. Use the CloudWatch alarm as the scaling policy for ASG

The Auto Scaling Group isn't tied to the metrics AWS exposes, also it can be any metric you want. It can be a custom metric.