# 4. Health Check

- Have X health checks failed => unhealthy (default 3)
- After X health checks passed => health (default 3)
- Default Health Check Interval: 30s (can set to 10s – higher cost)
- **About 15 health checkers will check the endpoint health**

    ⇒ one request every 2 seconds on average

- Can have HTTP, TCP and HTTPS health checks (no SSL verification)
- Possibility of integrating the health check with CloudWatch
- **Health checks can be linked to Route53 DNS queries!**