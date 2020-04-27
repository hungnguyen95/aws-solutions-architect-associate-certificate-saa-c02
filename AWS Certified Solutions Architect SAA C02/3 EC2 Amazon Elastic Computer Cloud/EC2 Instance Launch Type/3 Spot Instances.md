# 3. Spot Instances

Short workloads, for cheap, can lose instances (less reliable)

- Can get a discount of up to 90% compared to On-demand
- Define **max spot price** and get the instance while **current spot price < max**
    - The hourly spot price varies based on **offer** and **capacity**

    → The more people want a spot instance, obviously the more the price will go up.

    → If there is a greater capacity of spot instances then the price will go down.

    - If the **current spot price > your max price** you can choose to **stop** or **terminate** your instance with a 2 minutes grace period.

    Ex: Your max price: 50 cents / hour and current spot price is 70 cents / hour then the instance will have to be reclaimed by AWS. Either you can choose to stop your instance (you'll be able to  restart it later) or you can choose to terminate your instance and just be done with it. 

    So at any point of time, AWS can come to you and give you a notification and saying, you have only two minutes to deal with that instance, either stop it or terminate it, afterwards it will be ours.

- Other strategy: **Spot Block**
    - “block” spot instance during a specified time frame (1 to 6 hours) without interruptions

    Ex: You're saying I want to have that spot instance between 1 to 6 hours. So maybe I want it for 4 hours and I don't want you to interrupt me. So you're going to pay the price in advance, but at least know you're gonna get that discount, and on top of it your spot instances will not be interrupted.

    - In rare situations, the instance may be reclaimed

    → It's not as safe as On-Demand instance but still much safer than a regular spot instance.

    - **Used for batch jobs, data analysis, or workloads that are resilient to failures**
    - **Not great for critical jobs or databases**

![3%20Spot%20Instances/Untitled.png](3%20Spot%20Instances/Untitled.png)

---

![3%20Spot%20Instances/Untitled%201.png](3%20Spot%20Instances/Untitled%201.png)

---

# Spot fleets

- Spot fleets = set of spot instances + (optional) on-demand instances
- The Spot Fleet will try to meet the target capacity with price constraints
    - Define possible launch pools: instance type (m5.large), OS, AZ
    - Can have multiple launch pools, so that the fleet can choose
    - Spot Fleet stops launching instances when reaching capacity or max cost

- Strategies to allocate Spot Instances:
    - `lowestPrice`: from the pool with the lowest price (cost optimization, short workload)
    - `diversifed`: distributed across all pools (great for availability, long workloads)
    - `capacityOptimized`: pool with the optimal capacity for the number of instances

- Spot Fleets allow us to automatically request Spot Instances with the lowest price.