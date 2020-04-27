# 7. Serverless Solution Architecture

# Mobile App

- Serverless REST API: HTTPS, API Gateway, Lambda, DynamoDB
- Using Cognito to generate temporary credentials with STS to access S3bucket with restricted policy. App users can directly access AWS resources this way. Pattern can be applied to DynamoDB, Lambda, ...
- Caching the reads on DynamoDB using DAX
- Caching the REST requests at the API Gateway level
- Security for authentication and authorization with Cognito, STS

![7%20Serverless%20Solution%20Architecture/Untitled.png](7%20Serverless%20Solution%20Architecture/Untitled.png)

---

# Hosted Website

- We’ve seen static content being distributed using CloudFront with S3
- The REST API was serverless, didn’t need Cognito because public
- We leveraged a Global DynamoDB table to serve the data globally
- (we could have used Aurora Global Tables)
- We enabled DynamoDB streams to trigger a Lambda function
- The lambda function had an IAM role which could use SES
- SES (Simple Email Service) was used to send emails in a serverless way
- S3 can trigger SQS / SNS / Lambda to notify of events

![7%20Serverless%20Solution%20Architecture/Untitled%201.png](7%20Serverless%20Solution%20Architecture/Untitled%201.png)

---

# Micro Services

- You are free to design each micro-service the way you want
- Synchronous patterns: API Gateway, Load Balancers
- Asynchronous patterns: SQS, Kinesis, SNS, Lambda triggers (S3)
- Challenges with micro-services:
    - repeated overhead for creating each new microservice
    - issues with optimizing server density/utilization
    - complexity of running multiple versions of multiple microservices simultaneously
    - proliferation of client-side code requirements to integrate with many separate services
- Some of the challenges are solved by Serverless patterns
    - API Gateway, Lambda scale automatically and you pay per usage
    - You can easily clone API, reproduce environments
    - Generated client SDK through Swagger integration for the API Gateway

![7%20Serverless%20Solution%20Architecture/Untitled%202.png](7%20Serverless%20Solution%20Architecture/Untitled%202.png)

---

# Distributing paid content

- We have implemented a fully serverless solution:
    - Cognito for authentication
    - DynamoDB for storing users that are premium
    - 2 serverless applications
        - Premium User registration
        - CloudFront Signed URL generator
    - Content is stored in S3 (serverless and scalable)
    - Integrated with CloudFront with OAI for security (users can’t bypass)
    - CloudFront can only be used using Signed URLs to prevent unauthorized users
    - What about S3 Signed URL? They’re not efficient for global access

![7%20Serverless%20Solution%20Architecture/Untitled%203.png](7%20Serverless%20Solution%20Architecture/Untitled%203.png)

---

# Software updates offloading

### ⇒ Use CloudFront

- No changes to architecture
- Will cache software update files at the edge
- Software update files are not dynamic, they’re static (never changing)
- Our EC2 instances aren’t serverless
- But CloudFront is, and will scale for us
- Our ASG will not scale as much, and we’ll save tremendously in EC2
- We’ll also save in availability, network bandwidth cost, etc
- Easy way to make an existing application more scalable and cheaper!

![7%20Serverless%20Solution%20Architecture/Untitled%204.png](7%20Serverless%20Solution%20Architecture/Untitled%204.png)

---

# Big Data Ingestion Pipeline

- IoT Core allows you to harvest data from IoT devices
- Kinesis is great for real-time data collection
- Firehose helps with data delivery to S3 in near real-time (1 minute)
- Lambda can help Firehose with data transformations
- Amazon S3 can trigger notifications to SQS
- Lambda can subscribe to SQS (we could have connecter S3 to Lambda)
- Athena is a serverless SQL service and results are stored in S3
- The reporting bucket contains analyzed data and can be used by reporting tool such as AWS QuickSight, Redshift, etc…

![7%20Serverless%20Solution%20Architecture/Untitled%205.png](7%20Serverless%20Solution%20Architecture/Untitled%205.png)