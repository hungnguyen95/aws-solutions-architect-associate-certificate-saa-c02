# 7. Connection Draining

- CLB: Connection Draining
- Target Group: Deregistration Delay (for ALB & NLB)

- Time to complete "in-flight requests" while the instance is de-registering or unhealthy
- Stops sending new requests to the instance which is de-registering
- Between 1 to 3600 seconds, default is 300 seconds
- Can be disabled (set value to 0)
- Set to a low value if your requests are short

![7%20Connection%20Draining/Untitled.png](7%20Connection%20Draining/Untitled.png)