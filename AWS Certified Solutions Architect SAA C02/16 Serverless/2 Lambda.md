# 2. Lambda

# Lambda vs. EC2

- Virtual Servers in the Cloud
- Limited by RAM and CPU
- Continuously running
- Scaling means intervention to add / remove servers

    ![2%20Lambda/Untitled.png](2%20Lambda/Untitled.png)

- Virtual **functions** – no servers to manage!
- Limited by time - **short executions**

    ⇒ After call lambda function, they're done

- Run **on-demand**
- **Scaling is automated!**

    ![2%20Lambda/Untitled%201.png](2%20Lambda/Untitled%201.png)

---

# Benefits of AWS Lambda

- Easy Pricing:
    - Pay per request and compute time
    - Free tier of 1,000,000 AWS Lambda requests and 400,000 GBs of compute time
- Integrated with the whole AWS Stack
- Integrated with many programming languages
- Easy monitoring through AWS CloudWatch
- Easy to get more resources per functions (up to 3GB of RAM!)
- Increasing RAM will also improve CPU and network!

---

# AWS Lambda language support

- Node.js (JavaScript)
- Python
- Java (Java 8 compatible)
- C# (.NET Core)
- Golang
- C# / Powershell

---

# AWS Lambda Integrations

### Main ones

![2%20Lambda/Untitled%202.png](2%20Lambda/Untitled%202.png)

---

# Example: Serverless Thumbnail creation

![2%20Lambda/Untitled%203.png](2%20Lambda/Untitled%203.png)

---

# Example: Serverless CRON Job

![2%20Lambda/Untitled%204.png](2%20Lambda/Untitled%204.png)

---

# AWS Lambda Pricing

- Pay per **calls**:
    - First 1,000,000 requests are free
    - $0.20 per 1 million requests thereafter ($0.0000002 per request)
- Pay per **duration**: (in increment of 100ms)
    - 400,000 GB-seconds of compute time per month if FREE
    - == 400,000 seconds if function is 1GB RAM
    - == 3,200,000 seconds if function is 128 MB RAM
    - After that $1.00 for 600,000 GB-seconds
- It is usually **very cheap** to run AWS Lambda so it’s **very popular**

---

# AWS Lambda Configuration

- Timeout: default 3 seconds, max of 15 minutes (900 seconds)
- Environment variables
- Allocated memory (128M to 3G)
- Ability to deploy within a VPC + assign security groups
- IAM execution role must be attached to the Lambda function

---

# AWS Lambda Limits to Know

- Execution:
    - Memory allocation: 128 MB – 3008 MB (64 MB increments)
    - Maximum execution time: 300 seconds (5 minutes), now 15 minutes but 5 for exam
    - Disk capacity in the “function container” (in /tmp): 512 MB
    - Concurrency limits: 1000
- Deployment:
    - Lambda function deployment size (compressed .zip): 50 MB
    - Size of uncompressed deployment (code + dependencies): 250 MB
    - Can use the /tmp directory to load other files at startup
    - Size of environment variables: 4 KB

---

# Lambda@Edge

- You have deployed a CDN using CloudFront
- What if you wanted to run a global AWS Lambda alongside?
- Or how to implement request filtering before reaching your application?

- For this, you can use **Lambda@Edge**: deploy Lambda functions alongside your CloudFront CDN
    - Build more responsive applications
    - You don’t manage servers, Lambda is deployed globally
    - Customize the CDN content
    - Pay only for what you use

- You can use Lambda to change CloudFront requests and responses:
    - After CloudFront receives a request from a viewer (viewer request)
    - Before CloudFront forwards the request to the origin (origin request)
    - After CloudFront receives the response from the origin (origin response)
    - Before CloudFront forwards the response to the viewer (viewer response)

![2%20Lambda/Untitled%205.png](2%20Lambda/Untitled%205.png)

- You can also generate responses to viewers without ever sending the request to the origin

---

# Lambda@Edge: Global application

![2%20Lambda/Untitled%206.png](2%20Lambda/Untitled%206.png)