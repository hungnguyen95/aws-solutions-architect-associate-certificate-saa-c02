# 1. AWS SQS

![1%20AWS%20SQS/Untitled.png](1%20AWS%20SQS/Untitled.png)

- Have many producers send messages to SQS Queue
- Consumers poll messages from SQS Queue
- The number of consumers don't need to equal to the number of producers

---

# Standard Queue

- Oldest offering (over 10 years old)
- Fully managed
- Scales from 1 message per second to 10,000s per second
- Default retention of messages: 4 days, maximum of 14 days
- No limit to how many messages can be in the queue
- Low latency (<10 ms on publish and receive)
- Horizontal scaling in terms of number of consumers
- Can have duplicate messages (at least once delivery, occasionally)
- Can have out of order messages (best effort ordering)
- Limitation of 256KB per message sent

---

# Delay Queue

- Delay a message (consumers don’t see it immediately) up to 15 minutes
- Default is 0 seconds (message is available right away)
- Can set a default at queue level
- Can override the default using the **DelaySeconds** parameter

![1%20AWS%20SQS/Untitled%201.png](1%20AWS%20SQS/Untitled%201.png)

For e.g: the message will be in SQS for five minutes, waiting, and then, after five minutes, the consumer will be able to see that message.

---

# Producing Messages

- Define Body
- Add message attributes (metadata – optional)
- Provide Delay Delivery (optional) (**DelaySeconds**)
- Get back
    - Message identifier (Unique ID)
    - MD5 hash of the body

![1%20AWS%20SQS/Untitled%202.png](1%20AWS%20SQS/Untitled%202.png)

---

# Consuming Messages

- Poll SQS for messages (receive up to 10 messages at a time)
- Process the message within the visibility timeout
- Delete the message using the message ID & receipt handle

![1%20AWS%20SQS/Untitled%203.png](1%20AWS%20SQS/Untitled%203.png)

---

# Visibility timeout

- When a consumer polls a message from a queue, the message is “invisible” to other consumers for a defined period… the **Visibility Timeout**:
    - Set between 0 seconds and 12 hours (default 30 seconds)
    - If too high (15 minutes) and consumer fails to process the message, you must wait a long time before processing the message again
    - If too low (30 seconds) and consumer needs time to process the message (2 minutes), another consumer will receive the message and the message will be processed more than once
- **ChangeMessageVisibility** API to change the visibility while processing a message
- **DeleteMessage** API to tell SQS the message was successfully processed

---

# Dead Letter Queue

- If a consumer fails to process a message within the Visibility Timeout…the message goes back to the queue!
- We can set a threshold of how many times a message can go back to the queue – it’s called a "**redrive policy**"
- After the threshold is exceeded, the message goes into a dead letter queue (DLQ)
- We have to create a DLQ first and then designate it dead letter queue
- Make sure to process the messages in the DLQ before they expire

![1%20AWS%20SQS/Untitled%204.png](1%20AWS%20SQS/Untitled%204.png)

Example: After the consumer processed message and got error, it will go to failure loop and put the message back to SQS Queue. If the message is failure to process 3 times [**redive policy**] (maybe same consumer or different consumers), it will be put on Dead Letter Queue and we move on

Dead Letter Queue contains all problem messages and you can look at it and debug as you wish.

---

# Long Polling

- When a consumer requests message from the queue, it can optionally “wait” for messages to arrive if there are none in the queue
- This is called Long Polling
- **LongPolling decreases the number of API calls made to SQS while increasing the efficiency and latency of your application.**
- The wait time can be between 1 sec to 20 sec (20 sec preferable)
- Long Polling is preferable to Short Polling
- Long polling can be enabled at the queue level or at the API level using **WaitTimeSeconds**

![1%20AWS%20SQS/Untitled%205.png](1%20AWS%20SQS/Untitled%205.png)

Example: The consumer polls message from SQS Queue, and willing to wait 20 seconds.

No messages in SQS Queue → consumer is going to wait

Producer send a message right now, and so that message will be passed onto consumer, who's been waiting for maybe 5 or 10 seconds

⇒ Saved a ton of cost, because consumer waited, it didn't ask SQS every 30 miliseconds to get message.

---

# SQS Message consumption flow diagram

![1%20AWS%20SQS/Untitled%206.png](1%20AWS%20SQS/Untitled%206.png)

---

# FIFO Queue

- Newer offering (First In - First out) – not available in all regions!
- Name of the queue must end in `.fifo`
- Lower throughput (up to 3,000 per second with batching, 300/s without batching)
- Messages are processed in order by the consumer
- Messages are sent exactly once
- No per message delay (only per queue delay)
- Ability to do content based de-duplication
- 5-minute interval de-duplication using “Duplication ID”
- Message Groups:
    - Possibility to group messages for FIFO ordering using “Message GroupID”
    - Only one worker can be assigned per message group so that messages are processed in order
    - Message group is just an extra tag on the message

![1%20AWS%20SQS/Untitled%207.png](1%20AWS%20SQS/Untitled%207.png)

---

# SQS with Auto Scaling Group (ASG)

![1%20AWS%20SQS/Untitled%208.png](1%20AWS%20SQS/Untitled%208.png)

- EC2 instances with ASG are polling messages from SQS Queue
- EC2 instances are going to push a CloudWatch Custom Metric (maybe `queue length / number of instances`)
- If this metric goes above (or below) a certain threshold, that means have too many messages or not enough instances.
- We set the threshold, we will create a CloudWatch Alarm for breaching this metric, and it will automatically be assigned to a scaling policy on ASG and scale it.

---

# SQS to decouple between application tiers

![1%20AWS%20SQS/Untitled%209.png](1%20AWS%20SQS/Untitled%209.png)

- Decouple applications tiers
- One Application process requests and send message to SQS Queue
- Other Application poll message and process it