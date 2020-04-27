# 3. ECS

- ECS is a container orchestration service
- ECS helps you run Docker containers on EC2 machines
- ECS is complicated, and made of:
    - “ECS Core”: Running ECS on user-provisioned EC2 instances
    - Fargate: Running ECS tasks on AWS-provisioned compute (serverless)
    - EKS: Running ECS on AWS-powered Kubernetes (running on EC2)
    - ECR: Docker Container Registry hosted by AWS
- ECS & Docker are very popular for microservices
- IAM security and roles at the ECS task level

---

# Docker

- Docker is a “container technology"
- Run a containerized application on any machine with Docker installed
- **Containers allows our application to work the same way anywhere**
- Containers are isolated from each other
- Control how much memory / CPU is allocated to your container
- Ability to restrict network rules
- More efficient than Virtual machines
- Scale containers up and down very quickly (seconds)

---

# AWS ECS – Use cases

- Run microservices
    - Ability to run multiple docker containers on the same machine
    - Easy service discovery features to enhance communication
    - Direct integration with Application Load Balancers
    - Auto scaling capability

- Run batch processing / scheduled tasks
    - Schedule ECS containers to run on On-demand / Reserved / Spot instances

- Migrate applications to the cloud
    - Dockerize legacy applications running on premise
    - Move Docker containers to run on ECS

---

# AWS ECS – Concepts

- **ECS cluster:** set of EC2 instances
- **ECS service:** applications definitions running on ECS cluster
- **ECS tasks + definition**: containers running to create the application
- **ECS IAM roles**: roles assigned to tasks to interact with AWS

![3%20ECS/Untitled.png](3%20ECS/Untitled.png)

---

# AWS ECS – ALB integration

- Application Load Balancer (ALB) has a direct integration feature with ECS called “port mapping”
- This allows you to run multiple instances of the same application on the same EC2 machine
- Use cases:
    - Increased resiliency even if running on one EC2 instance
    - Maximize utilization of CPU / cores
    - Ability to perform rolling upgrades without impacting application uptime

![3%20ECS/Untitled%201.png](3%20ECS/Untitled%201.png)

---

# AWS ECS – ECS Setup & Config file

- Run an EC2 instance, install the ECS agent with ECS config file
- Or use an ECS-ready Linux AMI (still need to modify config file)
- ECS Config file is at **`/etc/ecs/ecs.config`**

![3%20ECS/Untitled%202.png](3%20ECS/Untitled%202.png)

---

# AWS ECR – Elastic Container Registry

- Store, managed and deploy your containers on AWS
- Fully integrated with IAM & ECS
- Sent over HTTPS (encryption in flight) and encrypted at rest

![3%20ECS/Untitled%203.png](3%20ECS/Untitled%203.png)

---

# ECS - IAM Task Roles

- The EC2 instance should have an IAM role allowing it to access the ECS service (for the ECS agent)
- Each ECS task should have an ECS IAM task role to perform their API calls
- Use the `taskRoleArn` parameter in a task definition

![3%20ECS/Untitled%204.png](3%20ECS/Untitled%204.png)

---

# Fargate

- When launching an ECS Cluster, we have to create our EC2 instances
- If we need to scale, we need to add EC2 instances
- So we manage infrastructure…

- With Fargate, it’s all Serverless!
- We don’t provision EC2 instances
- We just create task definitions, and AWS will run our containers for us
- To scale, just increase the task number. Simple! No more EC2!