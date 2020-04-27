# 9. Beanstalk

# Developer problems on AWS

- Managing infrastructure
- Deploying Code
- Configuring all the databases, load balancers, etc
- Scaling concerns

⇒ Most web apps have the same architecture (ALB + ASG)

Developer wants:

- All the developers want is for their code to run!
- Possibly, consistently across different applications and environments

---

# AWS Elastic Beanstalk Overview

- Elastic Beanstalk is a developer centric view of deploying an application on AWS
- It uses all the component’s we’ve seen before: EC2, ASG, ELB, RDS, etc
- But it’s all in one view that’s easy to make sense of!
- We still have full control over the configuration

- Beanstalk is free but you pay for the underlying instances

---

# Elastic Beanstalk

- Managed service
    - Instance configuration / OS is handled by Beanstalk
    - Deployment strategy is configurable but performed by Elastic Beanstalk

- Just the application code is the responsibility of the developer

- Three architecture models:
    - Single Instance deployment: good for dev
    - LB + ASG: great for production or pre-production web applications
    - ASG only: great for non-web apps in production (workers, etc..)

- Elastic Beanstalk has three components
    - Application
    - Application version: each deployment gets assigned a version

        → every time you upload new code, you'll get an application version

    - Environment name (dev, test, prod…): free naming
- You deploy application versions to environments and can promote application versions to the next environment
- Rollback feature to previous application version
- Full control over lifecycle of environments

![9%20Beanstalk/Untitled.png](9%20Beanstalk/Untitled.png)

---

# Elastic Beanstalk

- Support for many platforms
    - Go
    - Java SE
    - Java with Tomcat
    - .NET on Windows Server with IIS
    - Node.js
    - PHP
    - Python
    - Ruby
    - Packer Builder
    - Single Container Docker
    - Multicontainer Docker
    - Preconfigured Docker
- If not supported, you can write your custom platform (advanced)