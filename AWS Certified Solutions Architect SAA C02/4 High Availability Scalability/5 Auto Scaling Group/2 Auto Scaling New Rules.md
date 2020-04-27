# 2. Auto Scaling New Rules

- It is now possible to define ”better” auto scaling rules that are directly managed by EC2
    - Target Average CPU Usage

        You want to have a target average CPU usage in your Auto Scaling Group and basically, it will scale in and scale out based on your load to meet that target CPU usage.

    - Number of requests on the ELB per instance
    - Average Network In
    - Average Network Out

    → Whatever you think the better scaling policy is for your application, you can use it.

- These rules are easier to set up and can make more sense