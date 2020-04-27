# 1. CICD

# Continuous Integration

- Developers push the code to a code repository often (GitHub / CodeCommit /Bitbucket / etc…)
- A testing / build server checks the code as soon as it’s pushed (CodeBuild / Jenkins CI / etc…)
- The developer gets feedback about the tests and checks that have passed / failed
- Find bugs early, fix bugs
- Deliver faster as the code is tested
- Deploy often
- Happier developers, as they’re unblocked

![1%20CICD/Untitled.png](1%20CICD/Untitled.png)

---

# Continuous Delivery

- Ensure that the software can be released reliably whenever needed
- Ensures deployments happen often and are quick
- Shift away from "one release every 3 months" to "5 releases a day"
- That usually means automated deployment
    - CodeDeploy
    - Jenkins CD
    - Spinnaker
    - Etc...

![1%20CICD/Untitled%201.png](1%20CICD/Untitled%201.png)

---

# Technology Stack for CICD

![1%20CICD/Untitled%202.png](1%20CICD/Untitled%202.png)