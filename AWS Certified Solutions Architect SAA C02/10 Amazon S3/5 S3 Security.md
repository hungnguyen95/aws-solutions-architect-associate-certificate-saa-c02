# 5. S3 Security

- User based
    - IAM policies - which API calls should be allowed for a specific user from IAM console

- Resource based
    - Bucket Policies - bucket wide rules from the S3 console - allows cross account
    - Object Access Control List (ACL) – finer grain
    - Bucket Access Control List (ACL) – less common

---

# S3 Bucket Policies

- JSON based policies
    - Resources: buckets and objects (ARN: Amazon Resource Name)
    - Actions: Set of API to Allow or Deny
    - Effect: Allow / Deny
    - Principal: The account or user to apply the policy to
- Use S3 bucket for policy to:
    - Grant public access to the bucket
    - Force objects to be encrypted at upload
    - Grant access to another account (Cross Account)

- S3 Bucket Policy example

```jsx
{
  "Id": "Policy1583857303735",
  "Version": "2012-10-17",
  "Statement": [
		// Force upload object must be encrypted
    {
      "Sid": "Stmt1583857276160",
      "Action": [
        "s3:PutObject"
      ],
      "Effect": "Deny",
      "Resource": "arn:aws:s3:::hungproman",
      "Condition": {
        "Null": {
          "s3:x-amz-server-side-encryption": "true"
        }
      },
      "Principal": "*"
    },
		// Force upload object use SSE-S3 for encryption
    {
      "Sid": "Stmt1583857302874",
      "Action": [
        "s3:PutObject"
      ],
      "Effect": "Deny",
      "Resource": "arn:aws:s3:::hungproman",
      "Condition": {
        "StringNotEquals": {
          "s3:x-amz-server-side-encryption": "AES256"
        }
      },
      "Principal": "*"
    }
  ]
}
```

---

# S3 Security - Other

- Networking:
    - Supports VPC Endpoints (for instances in VPC without www internet)

        → Instances can access internally within private AWS network

- Logging and Audit:
    - S3 access logs can be stored in other S3 bucket

        Don't store access logs in same S3 bucket → recursive (log a access log)

    - API calls can be logged in AWS CloudTrail
- User Security:
    - MFA (multi factor authentication) can be required in versioned buckets to delete objects
    - Signed URLs: URLs that are valid only for a limited time (ex: premium video service for logged in users)