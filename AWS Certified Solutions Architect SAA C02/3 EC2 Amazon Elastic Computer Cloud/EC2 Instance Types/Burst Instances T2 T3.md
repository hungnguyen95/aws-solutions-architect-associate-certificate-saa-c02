# Burst Instances (T2/T3)

- AWS has the concept of burstable instances (T2/T3 machines)

    → When the instance is running, you get good performance. And then, sometimes maybe you need to process something very unexpected, maybe there's a spike of loading your application, and CPU goes to 100%. In this case, during the spikes, the CPU can do something called a **burst** and a **burst** is like a boost of power and CPU is very good during that burst.

    → But if your machine bursts it uses burst credits, and as you can expect, if the credits are all gone, then the CPU becomes bad of terrible

    → When the CPU is stopped bursting, you gain back the credits over time (accumulate)

- Burst means that overall, the instance has OK CPU performance.
- When the machine needs to process something unexpected (a spike in load for example), it can burst, and CPU can be VERY good.
- If the machine bursts, it utilizes “burst credits”
- If all the credits are gone, the CPU becomes BAD
- If the machine stops bursting, credits are accumulated over time
- Burstable instances can be amazing to handle unexpected traffic and getting the insurance that it will be handled correctly
- If your instance consistently runs low on credit, you need to move to adifferent kind of non-burstable instance

## **Credit Usage**

![Burst%20Instances%20T2%20T3/Untitled.png](Burst%20Instances%20T2%20T3/Untitled.png)

## **Credit Balance**

![Burst%20Instances%20T2%20T3/Untitled%201.png](Burst%20Instances%20T2%20T3/Untitled%201.png)

- When we see the CPU skyrockets, the credit usage is very high and the credit balance goes down.
- But after the CPU credit usage is done, we're not using it anymore, then we slowly gain back our credit balance into a normal zone.

⇒ Your have to be careful and obviously monitor the credit usage and balance over time, otherwise you may have surprises.

---

# CPU Credits

![Burst%20Instances%20T2%20T3/Untitled%202.png](Burst%20Instances%20T2%20T3/Untitled%202.png)

- The bigger instance, the faster you gonna earn credits

    → If you have bigger instance then you will earn credits faster

- The bigger instance, the better is going to be the CPU

    → If you have bigger instance then you will have higher performance of bursting CPU

---

# T2/T3 Unlimited

- Nov 2017: It is possible to have an “unlimited burst credit balance”

    → You can burst as long as you want but you're going to pay for it

- You pay extra money if you go over your credit balance, but you don’t lose in performance

    → You need to make sure that you don't burst for no reason

- So be careful, costs could go high if you’re not monitoring the health of your instances

Read more here: [https://aws.amazon.com/blogs/aws/new-t2-unlimitedgoing-beyond-the-burst-with-high-performance/](https://aws.amazon.com/blogs/aws/new-t2-unlimitedgoing-beyond-the-burst-with-high-performance/)