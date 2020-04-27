# 1. TTL (Time to Live)

- TTL is basically a way for web browser and clients to cache the response of a DNS query (not to overload the DNS)

![1%20TTL%20Time%20to%20Live/Untitled.png](1%20TTL%20Time%20to%20Live/Untitled.png)

- Web browser make a DNS request for `[myapp.mydomain.com](http://myapp.mydomain.com)` and the Route53 will send back IP `32.45.67.85` (A record)
- On top of it, it's going to also send back the TTL
- We can configure TTL
- The browser will cache that DNS request and the response for the TTL duration

→ Anytime we request `[myapp.mydomain.com](http://myapp.mydomain.com)` the web browser will just look internally, and in some cases, you will not ask Route53 again.

→ If we change IP (change A record) our cache will be updated **but only after the TTL has expired**

- **High TTL: (e.g. 24hr)**
    - Less traffic on DNS
    - Possibly outdated records
- **Low TTL: (e.g 60 s)**
    - More traffic on DNS
    - Records are outdated for less time
    - Easy to change records
- TTL is mandatory for each DNS record