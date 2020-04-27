# 4. ELB (Elastic Load Balancing)

- Load balancers are servers that forward internet traffic to multiple servers (EC2 Instances) downstream.

![4%20ELB%20Elastic%20Load%20Balancing/Untitled.png](4%20ELB%20Elastic%20Load%20Balancing/Untitled.png)

- Say we have 3 EC2 Instances and they have our application. Our load balancer is going to be in the middle and it's going to divert traffic from the users to some of these EC2 instances.

    My first user is going to go directly to my first EC2 Instance through the Load Balancer, and the EC2 Instance will respond something to the Load Balancer

    User 2 may do the same kind of request mechanism, but this time, the User 2 will be served in the backend by the second EC2 Instance. 

    And the User 3 will be served by the third EC2 Instance

    → The Users just interface with the single point of entry which is our Load Balancer, and in the backend we can scale our EC2 Instances and have many of them serve the traffic.

---

# Why we use Load Balancer?

- Spread load across multiple downstream instances
- Expose a single point of access (DNS) to your application

    We don't need to know all the backend EC2, we just need to know about the point of access, the host name of load balancer.

- Seamlessly handle failures of downstream instances through **Health Check**
- Do regular health checks to your instances

    Load Balancer is going to regular health checks on your instances → it knows when not to send traffic to your instances.

- Provide SSL termination (HTTPS) for your websites

    → Provide you SSL or HTTPS security for your website directly on load balancer site.

- Enforce stickiness with cookies
- High availability across Availability Zones
- Separate public traffic from private traffic

---

# Why use an EC2 Load Balancer?

- An ELB (EC2 Load Balancer) is a managed load balancer
    - AWS guarantees that it will be working
    - AWS takes care of upgrades, maintenance, high availability
    - AWS provides only a few configuration knobs
- It costs less to setup your own load balancer but it will be a lot more effort on your end
- It is integrated with many AWS offerings / services

---

# Health Checks

- Health Checks are crucial for Load Balancers
- They enable the load balancer to know if instances it forwards traffic to are available to reply to requests
- The health check is done on a port and a route (/health is common)
- If the response is not 200 (OK), then the instance is unhealthy

![4%20ELB%20Elastic%20Load%20Balancing/Untitled%201.png](4%20ELB%20Elastic%20Load%20Balancing/Untitled%201.png)

- Here I show you a classic load balancer, will be doing a health check on your EC2 Instance on Port 4567 on the route /health, and if the EC2 Instance says 200 OK, it means I'm healthy. And if it's not, it will stop sending traffic.

    Health check happen every 5 secs and you can also configure that.

---

# Types of Load Balancer on AWS

- AWS has 3 kinds of managed Load Balancers
- Classic Load Balancer (v1 - old generation) – 2009
    - HTTP, HTTPS, TCP
- Application Load Balancer (v2 - new generation) – 2016
    - HTTP, HTTPS, WebSocket
- Network Load Balancer (v2 - new generation) – 2017
    - TCP, TLS (secure TCP) & UDP
- Overall, it is recommended to use the newer / v2 generation load balancers as theyprovide more features
- You can setup internal (private) or external (public) ELBs
    - Internal: It's private within your account and you cannot access it from the public web
    - External: public load balancer or ELB and this will allow your users to access

---

# Load Balancer Security Groups

![4%20ELB%20Elastic%20Load%20Balancing/Untitled%202.png](4%20ELB%20Elastic%20Load%20Balancing/Untitled%202.png)

- You have your users talking to your load balancer talking to your EC2 Instance. And your users may be talking to your load balancer through HTTPS or HTTP from anywhere.
- We should set something like this

    **Load balancer security group:**

![4%20ELB%20Elastic%20Load%20Balancing/Untitled%203.png](4%20ELB%20Elastic%20Load%20Balancing/Untitled%203.png)

- We allow HTTP on Port 80 of source 0.0.0.0/0 which means from anywhere. So any HTTP (Port 80) or HTTPS (Port 443) from anywhere can access to our load balancer.

![4%20ELB%20Elastic%20Load%20Balancing/Untitled%204.png](4%20ELB%20Elastic%20Load%20Balancing/Untitled%204.png)

- So from Load Balancer to EC2 Instance, we want the traffic to be restricted to your load balancer (only traffic from load balancer can send to EC2 instance, other traffic cannot). An as such, we can have an application security group which allows only traffic from the load balancer.

    **Application Security Group: Allow traffic only from Load Balancer**

    ![4%20ELB%20Elastic%20Load%20Balancing/Untitled%205.png](4%20ELB%20Elastic%20Load%20Balancing/Untitled%205.png)

- The source of security group which is also a security group, you see there is a long security group with an ID. And, that security group ID represents the load balancer security group ID.

    → So, the load balancer has a security group, your EC2 Instance has a security group. The EC2 Instance security group references the one from the load balancer

---

# Good to Know

- LBs can scale but not instantaneously – contact AWS for a “warm-up”
- Troubleshooting
    - 4xx errors are client induced errors
    - 5xx errors are application induced errors
    - Load Balancer Errors 503 means at capacity or no registered target
    - If the LB can’t connect to your application, check your security groups!
- Monitoring
    - ELB access logs will log all access requests (so you can debug per request)
    - CloudWatch Metrics will give you aggregate statistics (ex: connections count)

---

# Types of Load Balancer

[1. Classic Load Balancers (v1)](4%20ELB%20Elastic%20Load%20Balancing/1%20Classic%20Load%20Balancers%20v1.md)

[2. Application Load Balancer (v2)](4%20ELB%20Elastic%20Load%20Balancing/2%20Application%20Load%20Balancer%20v2.md)

[3. Network Load Balancer (v2)](4%20ELB%20Elastic%20Load%20Balancing/3%20Network%20Load%20Balancer%20v2.md)

[4. Load Balancer Stickiness](4%20ELB%20Elastic%20Load%20Balancing/4%20Load%20Balancer%20Stickiness.md)

[5. Cross zone balancing](4%20ELB%20Elastic%20Load%20Balancing/5%20Cross%20zone%20balancing.md)

[6. SSL/TLS](4%20ELB%20Elastic%20Load%20Balancing/6%20SSL%20TLS.md)

[7. Connection Draining](4%20ELB%20Elastic%20Load%20Balancing/7%20Connection%20Draining.md)