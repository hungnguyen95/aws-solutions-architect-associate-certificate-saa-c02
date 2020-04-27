# 5. IAM Roles and Resources Based Policies

- Attach a policy to a resource (example: S3 bucket policy) versus attaching of a using a role as a proxy

![5%20IAM%20Roles%20and%20Resources%20Based%20Policies/Untitled.png](5%20IAM%20Roles%20and%20Resources%20Based%20Policies/Untitled.png)

- When you assume a role (user, application or service), you give up your original permissions and take the permissions assigned to the role
- When using a resource based policy, the principal doesn’t have to give up his permissions
- Example: User in account A needs to scan a DynamoDB table in Account A and dump it in an S3 bucket in Account B.
- Supported by: Amazon S3 buckets, SNS topics, SQS queues