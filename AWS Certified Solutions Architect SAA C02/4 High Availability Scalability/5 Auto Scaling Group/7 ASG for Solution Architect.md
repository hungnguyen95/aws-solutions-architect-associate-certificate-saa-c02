# 7. ASG for Solution Architect

- ASG Default Termination Policy(simplified version):
    1. Find the AZ which has the most number of instances
    2. If there are multiple instances in the AZ to choose from, delete the one with the oldest launch configuration

    For e.g: On our scaling group, we have 2 AZs, and the first one, in A, we have 2 instances with V1 and 2 instances with V2 of our launch configuration. On the AZ B, we have 3 instances of V1 and V1 is the oldest launch configuration

    → The rule is that the auto scaling group will choose AZ A as the instance as the AZ were to delete instances because it is the one with the most instances.

![7%20ASG%20for%20Solution%20Architect/Untitled.png](7%20ASG%20for%20Solution%20Architect/Untitled.png)

- ASG tries the balance the number of instances across AZ by default

![7%20ASG%20for%20Solution%20Architect/Untitled%201.png](7%20ASG%20for%20Solution%20Architect/Untitled%201.png)

---

# Lifecycle Hooks

![7%20ASG%20for%20Solution%20Architect/Untitled%202.png](7%20ASG%20for%20Solution%20Architect/Untitled%202.png)

- By default as soon as an instance is launched in an ASG it’s in service

    But there is a long process of things that are happening when you launch a instance. So when your instance is launched you go to pending state, and if you define a lifecycle hook in the pending state, the instance will go directly into **pending: wait** state.

    And you have the option to configure that instance or do a lot of things, and then when you're ready, you move it into **pending: proceed**.

    When it goes into **pending: proceed**, it will go directly in being in service.

- You have the ability to perform extra steps before the instance goes in service (Pending state)

    → If there is no lifecycle hook, then you will go directly from pending to in service]

    The idea here is that you have the option to install extra software, do extra checks before making sure your instance is declared in service.

- When there is a scale in event, when the instance gets terminated, it goes into a terminating state.
- You have the ability to perform some actions before the instance is terminated (Terminating state)

    If you define a lifecycle hook on the terminating state, then you will go into the **terminating: wait**, then **terminating: proceed**, then finally **terminated**.

    → When you want to extract information (logs, files) before it is completed terminating.