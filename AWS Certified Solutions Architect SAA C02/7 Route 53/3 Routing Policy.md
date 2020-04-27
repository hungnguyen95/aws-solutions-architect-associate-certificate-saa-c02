# 3. Routing Policy

# Simple Routing Policy

- Maps a domain to one URL
- Use when you need to redirect to asingle resource
- You can’t attach health checks to simple routing policy
- **If multiple values are returned, a random one is chosen by the client**

![3%20Routing%20Policy/Untitled.png](3%20Routing%20Policy/Untitled.png)

---

# Weighted Routing Policy

- Control the % of the requests that go to specific endpoint
- Helpful to test 1% of traffic on new app version for example
- Helpful to split traffic between two regions
- Can be associated with Health Checks

![3%20Routing%20Policy/Untitled%201.png](3%20Routing%20Policy/Untitled%201.png)

---

# Latency Routing Policy

- Redirect to the server that has the least latency close to us
- Super helpful when latency of users is a priority
- **Latency is evaluated in terms of user to designated AWS Region**
- Germany may be directed to the US (if that’s thelowest latency)

![3%20Routing%20Policy/Untitled%202.png](3%20Routing%20Policy/Untitled%202.png)

---

# Failover Routing Policy

![3%20Routing%20Policy/Untitled%203.png](3%20Routing%20Policy/Untitled%203.png)

When browser does a DNS request → Route53 will give it is either the primary if the health check works, but if the health check doesn't pass, then automatically Route53 send back the secondary disaster recovery response back to the web browser

---

# Geo Location Routing Policy

- Geo Location Routing Policy
- **This is routing based on user location**
- Here we specify: traffic from the UK should go to this specific IP
- Should create a “default” policy (in case there’s no match onlocation)

![3%20Routing%20Policy/Untitled%204.png](3%20Routing%20Policy/Untitled%204.png)

---

# Multi Value Routing Policy

- Use when routing traffic to multiple resources
- Want to associate a Route 53 health checks with records
- Up to 8 healthy records are returned for each Multi Value query
- **Multi Value is not a substitute for having an ELB**

    → It's not substitute, but it helps to do some kind of load balancing as well on the client side.

![3%20Routing%20Policy/Untitled%205.png](3%20Routing%20Policy/Untitled%205.png)