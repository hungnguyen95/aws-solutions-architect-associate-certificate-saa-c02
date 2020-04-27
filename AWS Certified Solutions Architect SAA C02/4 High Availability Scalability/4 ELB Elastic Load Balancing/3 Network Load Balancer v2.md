# 3. Network Load Balancer (v2)

- Network load balancers (Layer 4) allow to:
    - **Forward TCP & UDP traffic to your instances**
    - Handle millions of request per seconds
    - Less latency ~100 ms (vs 400 ms for ALB)
- **NLB has one static IP per AZ, and supports assigning Elastic IP**(helpful for whitelisting specific IP)

    NLBs expose one static IP per Availability Zone on the outside and that's very helpful when you want to whitelist specific IP, and also they support assigning elastic IPs instead of getting the ones given by NLB itself.

    → That is different from the ALB or CLB, which did not have a static IP but had a static hostname.

- NLB are used for extreme performance, TCP or UDP traffic
- Not included in the AWS free tier

![3%20Network%20Load%20Balancer%20v2/Untitled.png](3%20Network%20Load%20Balancer%20v2/Untitled.png)

- No Security Group when we create NLB
- The instances don't see the traffic come from NLB, they see the traffic coming from the outside