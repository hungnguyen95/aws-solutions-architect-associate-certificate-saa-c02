# 4. Load Balancer Stickiness

- It is possible to implement stickiness so that the same client is always redirected to the same instance behind a load balancer
- This works for Classic Load Balancers & Application Load Balancers
- The “cookie” used for stickiness has an expiration date you control

    There's a cookie that is being used for the stickiness and the cookie has an expiration date and as long as the cookie remains the same, then the load balancer will redirect to the right instance.

- Use case: make sure the user doesn’t lose his session data
- Enabling stickiness may bring imbalance to the load over the backend EC2 instances
- For E.x: You have your load balancer and your EC2 Instances are in the backend, and we have our fist client, and it wants to talk to the load balancer, which will redirect to the EC2 instance on the left side.

![4%20Load%20Balancer%20Stickiness/Untitled.png](4%20Load%20Balancer%20Stickiness/Untitled.png)

- If the same client talks again to the load balancer with stickiness **enabled,** then the same EC2 instance will receive the same results.

![4%20Load%20Balancer%20Stickiness/Untitled%201.png](4%20Load%20Balancer%20Stickiness/Untitled%201.png)

- And so on, for client B and client C, then it may talk to the second EC2 Instance and if it does then it will always go to the second EC2 instance.

![4%20Load%20Balancer%20Stickiness/Untitled%202.png](4%20Load%20Balancer%20Stickiness/Untitled%202.png)

- Stickiness is very helpful if you want the same request originating from the same client, to go the same target.