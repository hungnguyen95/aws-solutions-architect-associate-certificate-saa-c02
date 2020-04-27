# 1. Vertical Scalability

- Vertically scalability means increasing the size of the instance

![1%20Vertical%20Scalability/Untitled.png](1%20Vertical%20Scalability/Untitled.png)

- E.x: We have a junior operator and we just hired him. He's great but he can only take 5 calls per minute. Now we have a senior operator and he's much greater. He can take up to 10 calls per minute. We've basically scaled up our junior into senior operator and he's faster and better.
- For example, your application runs on a t2.micro
- Scaling that application vertically means running it on a t2.large
- Vertical scalability is very common for non distributed systems, such as a database
- RDS, ElasticCache are services that can scale vertically.
- There’s usually a limit to how much you can vertically scale (hardware limit)