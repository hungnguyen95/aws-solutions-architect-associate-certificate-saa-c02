# 4. ASG Brain Dump

- Scaling policies can be on CPU, Network… and can even be on custom metrics or based on a schedule (if you know your visitors patterns)
- ASGs use Launch configurations and you update an ASG by providing a new launch configuration
- IAM roles attached to an ASG will get assigned to EC2 instances
- ASG are free. You pay for the underlying resources being launched
- Having instances under an ASG means that if they get terminated for whatever reason, the ASG will restart them. Extra safety!

    If you accidentally terminate an instance, the ASG will automatically create a new one or restart them.

- ASG can terminate instances marked as unhealthy by an LB (and hence replace them)