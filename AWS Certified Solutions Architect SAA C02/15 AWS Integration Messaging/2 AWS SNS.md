# 2. AWS SNS

- What if you want to send one message to many receivers?

![2%20AWS%20SNS/Untitled.png](2%20AWS%20SNS/Untitled.png)

- The “event producer” only sends message to one SNS topic
- As many “event receivers” (subscriptions) as we want to listen to the SNS topic notifications
- Each subscriber to the topic will get all the messages (note: new feature to filter messages)
- Up to 10,000,000 subscriptions per topic
- 100,000 topics limit
- Subscribers can be:
    - SQS
    - HTTP / HTTPS (with delivery retries – how many times)
    - Lambda
    - Emails
    - SMS messages
    - Mobile Notifications

---

# SNS integrates with a lot of Amazon Products

- Some services can send data directly to SNS for notifications
- CloudWatch (for alarms)
- Auto Scaling Groups notifications
- Amazon S3 (on bucket events)
- CloudFormation (upon state changes => failed to build, etc)
- Etc…

---

# AWS SNS – How to publish

- Topic Publish (within your AWS Server – using the SDK)
    - Create a topic
    - Create a subscription (or many)
    - Publish to the topic

- Direct Publish (for mobile apps SDK)
    - Create a platform application
    - Create a platform endpoint
    - Publish to the platform endpoint
    - Works with Google GCM, Apple APNS, Amazon ADM…

---

# SNS + SQS: Fan Out

![2%20AWS%20SNS/Untitled%201.png](2%20AWS%20SNS/Untitled%201.png)

- Push once in SNS, receive in many SQS
- Fully decoupled
- No data loss
- Ability to add receivers of data later
- SQS allows for delayed processing
- SQS allows for retries of work
- May have many workers on one queue and one worker on the other queue