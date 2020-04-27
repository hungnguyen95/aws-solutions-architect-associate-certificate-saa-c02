# 4. API Gateway

# Building a Serverless API

![4%20API%20Gateway/Untitled.png](4%20API%20Gateway/Untitled.png)

---

# AWS API Gateway

- AWS Lambda + API Gateway: No infrastructure to manage
- Handle API versioning (v1, v2…)
- Handle different environments (dev, test, prod…)
- Handle security (Authentication and Authorization)
- Create API keys, handle request throttling
- Swagger / Open API import to quickly define APIs
- Transform and validate requests and responses
- Generate SDK and API specifications
- Cache API responses

---

# API Gateway Integrations

- Outside of VPC:
    - AWS Lambda (most popular / powerful)
    - Endpoints on EC2
    - Load Balancers
    - Any AWS Service
    - External and publicly accessible HTTP endpoints

- Inside of VPC:
    - AWS Lambda in your VPC
    - EC2 endpoints in your VPC

---

# API Gateway – Security

## IAM Permissions

- Create an IAM policy authorization and attach to User / Role
- API Gateway verifies IAM permissions passed by the calling application
- Good to provide access within your own infrastructure
- Leverages “Sig v4” capability where IAM credential are in headers

![4%20API%20Gateway/Untitled%201.png](4%20API%20Gateway/Untitled%201.png)

## Lambda Authorizer (formerly Custom Authorizers)

- Uses AWS Lambda to validate the token in header being passed
- Option to cache result of authentication
- Helps to use OAuth / SAML / 3rd party type of authentication
- Lambda must return an IAM policy for the user

![4%20API%20Gateway/Untitled%202.png](4%20API%20Gateway/Untitled%202.png)

## Cognito User Pools

- Cognito fully manages user lifecycle
- API gateway verifies identity automatically from AWS Cognito
- No custom implementation required
- Cognito only helps with authentication, not authorization

![4%20API%20Gateway/Untitled%203.png](4%20API%20Gateway/Untitled%203.png)

## Summary

- **IAM:**
    - Great for users / roles already within your AWS account
    - Handle authentication + authorization
    - Leverages Sig v4
- **Custom Authorizer:**
    - Great for 3rd party tokens
    - Very flexible in terms of what IAM policy is returned
    - Handle Authentication + Authorization
    - Pay per Lambda invocation
- **Cognito User Pool:**
    - You manage your own user pool (can be backed by Facebook, Google login etc…)
    - No need to write any custom code
    - Must implement authorization in the backend