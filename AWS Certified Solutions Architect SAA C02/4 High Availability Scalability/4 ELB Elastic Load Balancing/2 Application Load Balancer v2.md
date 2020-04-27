# 2. Application Load Balancer (v2)

- Application load balancers is Layer 7 (HTTP)
- Load balancing to multiple HTTP applications across machines(target groups)
- Load balancing to multiple applications on the same machine(ex: containers)
- Support for HTTP/2 and WebSocket
- Support redirects (from HTTP to HTTPS for example)
- Routing tables to different target groups:
    - Routing based on path in URL ([example.com/users](http://example.com/users) & [example.com/posts](http://example.com/posts))

    → You can redirect these different two routes into different target groups.

    - Routing based on hostname in URL ([one.example.com](http://one.example.com/) & [other.example.com](http://other.example.com/))
    - Routing based on Query String, Headers

        (example.com/users?id=123&order=false)

- ALB are a great fit for micro services & container-based application(example: Docker & Amazon ECS)
- Has a port mapping feature to redirect to a dynamic port in ECS
- In comparison, we’d need multiple Classic Load Balancer per application

    If we wanted to have multiple applications behind a classic balancer, we have to have multiple Classic Load Balancer, we would need to actually have one CLB per application, whereas we've able to have one application load balancer in front of many applications

![2%20Application%20Load%20Balancer%20v2/Untitled.png](2%20Application%20Load%20Balancer%20v2/Untitled.png)

- We have our external application load balancer, it's public facing and behind it we have **first Target Group** made of EC2 and this one is going to be routing from **Route/user**

    And we have **second Target Group** made of EC2 instances again, and this one is going to be our Search application (**Route/search**)

    As you can see here, we have two independent micro services that do different things.

    The first one is the user application, the second one is a search application → But they're behind the same Application Load Balancer.

---

# Target Groups

- EC2 instances (can be managed by an Auto Scaling Group) – HTTP
- ECS tasks (managed by ECS itself) – HTTP
- Lambda functions – HTTP request is translated into a JSON event
- IP Addresses – must be private IPs
- ALB can route to multiple target groups
- Health checks are at the target group level

---

# Good to know

- Fixed hostname ([XXX.region.elb.amazonaws.com](http://xxx.region.elb.amazonaws.com/))
- The application servers don’t see the IP of the client directly
    - The true IP of the client is inserted in the header **X-Forwarded-For**
    - We can also get Port (**X-Forwarded-Port**) and proto (**X-Forwarded-Proto**)

![2%20Application%20Load%20Balancer%20v2/Untitled%201.png](2%20Application%20Load%20Balancer%20v2/Untitled%201.png)