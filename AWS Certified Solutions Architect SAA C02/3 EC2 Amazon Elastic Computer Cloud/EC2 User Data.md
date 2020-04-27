# EC2 User Data

- It is possible to bootstrap our instances using an EC2 User data script.
- bootstrapping means launching commands when a machine starts
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
    - Installing updates
    - Installing software
    - Downloading common files from the internet
    - Anything you can think of

- The EC2 User Data runs with the root user

→ We can create User Data when configure EC2 Instance

→ User data must have `#!/bin/bash` in first line

![EC2%20User%20Data/Untitled.png](EC2%20User%20Data/Untitled.png)