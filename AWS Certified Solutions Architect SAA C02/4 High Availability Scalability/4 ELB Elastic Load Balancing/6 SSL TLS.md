# 6. SSL/TLS

- An SSL Certificate allows traffic between your clients and your load balancer to be encrypted in transit (in-flight encryption)
- **SSL** refers to Secure Sockets Layer, used to encrypt connections
- **TLS** refers to Transport Layer Security, which is a newer version
- Nowadays, **TLS certificates are mainly used**, but people still refer as SSL
- Public SSL certificates are issued by Certificate Authorities (CA)
- Comodo, Symantec, GoDaddy, GlobalSign, Digicert, Letsencrypt, etc…

    And using this public SSL certificate attached to our load balancer, we're able to encrypt the connection between the clients and the load balancer

- SSL certificates have an expiration date (you set) and must be renewed

---

# Load Balancer - SSL Certificates

![6%20SSL%20TLS/Untitled.png](6%20SSL%20TLS/Untitled.png)

- Users connect over HTTPS (using SSL certificates and it's encrypted, it's secure and it connects over the public internet) to your balancer.
- The load balancer uses an X.509 certificate (SSL/TLS server certificate)
- You can manage certificates using ACM (AWS Certificate Manager)
- You can create upload your own certificates alternatively
- HTTPS listener:
    - You must specify a default certificate
    - You can add an optional list of certs to support multiple domains
    - **Clients can use SNI (Server Name Indication) to specify the hostname they reach**
    - Ability to specify a security policy to support older versions of SSL / TLS (legacy clients)

---

# SSL – Server Name Indication (SNI)

- SNI solves the problem of loading **multiple SSL certificates onto one web server** (to serve multiple websites)
- It’s a “newer” protocol, and requires the client to **indicate** the hostname of the target server in the initial SSL handshake

    So the client will say "I want to connect to this website" and the server will know what certificate to load. And this a newer protocol, not every client support this.

- The server will then find the correct certificate, or return the default one

**Note:**

- Only works for ALB & NLB (newer generation), CloudFront
- Does not work for CLB (older gen)

For example, we have our ALB here, and we have 2 target groups. The first one is `[www.mycorp.com](http://www.mycorp.com)` and the rest is `[Domain1.example.com](http://domain1.example.com)` . So the ALB will be routing to these target groups based on some rules, and the rules may be directly linked in this case, to the hostname.

![6%20SSL%20TLS/Untitled%201.png](6%20SSL%20TLS/Untitled%201.png)

We also have two SSL certificates: `[doamain1.example.com](http://doamain1.example.com)` and `[www.mycorp.com](http://www.mycorp.com)` which corresponds to the corresponding target groups. 

- Now the clients connects to our ALB and say "I would like `[www.mycorp.com](http://www.mycorp.com)` and that is part of server name indication

![6%20SSL%20TLS/Untitled%202.png](6%20SSL%20TLS/Untitled%202.png)

- And the ALB says "I've seen that you want `[mycorp.com](http://mycorp.com)` , let me use the correct SSL certificates to fill that request"

![6%20SSL%20TLS/Untitled%203.png](6%20SSL%20TLS/Untitled%203.png)

- So it's going to take the right SSL certificates, encrypt the traffic and then thanks to the rules, it's going to know, to redirect to the correct target group `[mycorp.com](http://mycorp.com)`

![6%20SSL%20TLS/Untitled%204.png](6%20SSL%20TLS/Untitled%204.png)

- And obviously if you have another client connecting to your ALB for `[Domain1.example.com](http://domain1.example.com)` then you will be able to pull the right SSL certificate again and connected to the right target group.

![6%20SSL%20TLS/Untitled%205.png](6%20SSL%20TLS/Untitled%205.png)

→ So using SNI (Server Name Indication) you are able to have multiple target groups for different websites using different SSL certificates.

---

## Classic Load Balancer (v1)

- Support only one SSL certificate
- Must use multiple CLB for multiple hostname with multiple SSL certificates

## Application Load Balancer (v2)

- Supports multiple listeners with multiple SSL certificates
- Uses Server Name Indication (SNI) to make it work

## Network Load Balancer (v2)

- Supports multiple listeners with multiple SSL certificates
- Uses Server Name Indication (SNI) to make it work