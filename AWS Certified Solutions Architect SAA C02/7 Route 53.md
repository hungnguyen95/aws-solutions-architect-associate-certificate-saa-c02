# 7. Route 53

- Route53 is a Managed DNS (Domain Name System)
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
- In AWS, the most common records are:
    - A: URL to IPv4
    - AAAA: URL to IPv6
    - CNAME: URL to URL
    - Alias: URL to AWS resource

---

# Diagram for A Record

![7%20Route%2053/Untitled.png](7%20Route%2053/Untitled.png)

- Step 1: Browser will make an DNS request say for `[myapp.mydomain.com](http://myapp.mydomain.com)` and the Route53
- Step 2: Route53 will reply and say by the way in my records it looks like this domain has this IP address in A record. So URL to IP mapping and I send back the IP `32.35.67.85`
- Step 3: Browser has done this DNS request and has gotten back an IP from it. Now it knows directly to make an HTTP request directly to the IP and it will reach the application server. And it will say, by the way, the host name it asked for is `myapp.mydomain.com`
- Step 4: The application server will reply HTTP response.

---

# Overview

- Route53 can use:
    - public domain names you own (or buy)

        [application1.mypublicdomain.com](http://application1.mypublicdomain.com/)

    - private domain names that can be resolved by your instances in your VPCs

        application1.company.internal

- Route53 has advanced features such as:
    - Load balancing (through DNS – also called client load balancing)
    - Health checks (although limited…)
    - Routing policy: simple, failover, geolocation, latency, weighted, multi value
- You pay $0.50 per month per hosted zone

---

[1. TTL (Time to Live)](7%20Route%2053/1%20TTL%20Time%20to%20Live.md)

[2. CNAME and ALIAS](7%20Route%2053/2%20CNAME%20and%20ALIAS.md)

[3. Routing Policy](7%20Route%2053/3%20Routing%20Policy.md)

[4. Health Check](7%20Route%2053/4%20Health%20Check.md)

[5. Route53 as a Registrar](7%20Route%2053/5%20Route53%20as%20a%20Registrar.md)