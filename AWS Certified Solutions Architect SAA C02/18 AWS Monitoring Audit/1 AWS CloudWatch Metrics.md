# 1. AWS CloudWatch Metrics

- CloudWatch provides metrics for *every* services in AWS
- **Metric** is a variable to monitor (CPUUtilization, NetworkIn…)
- Metrics belong to **namespaces**
- **Dimension** is an attribute of a metric (instance id, environment, etc…)
- Up to 10 dimensions per metric
- Metrics have **timestamps**
- Can create CloudWatch dashboards of metrics

---

# AWS CloudWatch EC2 Detailed monitoring

- EC2 instance metrics have metrics "every 5 minutes"
- With detailed monitoring (for a cost), you get data “every 1 minute”
- Use detailed monitoring if you want to more prompt scale your ASG!
- The AWS Free Tier allows us to have 10 detailed monitoring metrics
- Note: EC2 Memory usage is by default not pushed (must be pushed from inside the instance as a custom metric)

---

# AWS CloudWatch Custom Metrics

- Possibility to define and send your own custom metrics to CloudWatch
- Ability to use dimensions (attributes) to segment metrics
    - Instance.id
    - Environment.name
- Metric resolution (`StorageResolution` API parameter – two possible value):
    - Standard: 1 minute (60 seconds)
    - High Resolution: 1 second – Higher cost
- Use API call `PutMetricData`
- Use exponential back off in case of throttle errors

---

# CloudWatch Dashboards

- Great way to setup dashboards for quick access to keys metrics
- **Dashboards are global**
- **Dashboards can include graphs from different regions**
- You can change the time zone & time range of the dashboards
- You can setup automatic refresh (10s, 1m, 2m, 5m, 15m)
- Pricing:
    - 3 dashboards (up to 50 metrics) for free
    - $3/dashboard/month afterwards

---

# AWS CloudWatch Logs

- Applications can send logs to CloudWatch using the SDK
- CloudWatch can collect log from:
    - Elastic Beanstalk: collection of logs from application
    - ECS: collection from containers
    - AWS Lambda: collection from function logs
    - VPC Flow Logs: VPC specific logs
    - API Gateway
    - CloudTrail based on filter
    - CloudWatch log agents: for example on EC2 machines
    - Route53: Log DNS queries
- CloudWatch Logs can go to:
    - Batch exporter to S3 for archival

        ⇒ Save logs to S3

    - Stream to ElasticSearch cluster for further analytics
- Logs storage architecture:
    - **Log groups**: arbitrary name, usually representing an application
    - **Log stream**: instances within application / log files / containers
- Can define log expiration policies (never expire, 30 days, etc..)

    ⇒ Because save log in CloudWatch will cost money (move to S3)

- Using the AWS CLI we can tail CloudWatch logs
- To send logs to CloudWatch, make sure IAM permissions are correct!
- Security: encryption of logs using KMS at the Group Level

---

# CloudWatch Logs Metric Filter & Insights

- CloudWatch Logs can use filter expressions
    - For example, find a specific IP inside of a log
    - Metric filters can be used to trigger alarms
- CloudWatch Logs Insights (new – Nov 2018) can be used to query logs and add queries to CloudWatch Dashboards

---

# AWS CloudWatch Alarms

- Alarms are used to trigger notifications for any metric
- Various options (sampling, %, max, min, etc…)
- Alarm States:
    - OK
    - INSUFFICIENT_DATA
    - ALARM
- Period:
    - Length of time in seconds to evaluate the metric
    - High resolution custom metrics: can only choose 10 sec or 30 sec

    ⇒ 1 datapoint = 1 period

    ⇒ For e.g: period 5 mins → Get data every 5 mins, average (or other function like min, max, ...) all data within 5 mins → 1 datapoint.

---

# AWS CloudWatch Events

- Schedule: Cron jobs
- Event Pattern: Event rules to react to a service doing something
    - Ex: CodePipeline state changes!
- Triggers to Lambda functions, SQS/SNS/Kinesis Messages
- CloudWatch Event creates a small JSON document to give information about the change