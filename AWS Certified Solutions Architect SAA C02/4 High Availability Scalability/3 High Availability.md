# 3. High Availability

- High Availability usually goes hand in hand with horizontal scaling
- High availability means running your application / system in at least 2 datacenters (== Availability Zones)
- The goal of high availability is to survive a data center loss

![3%20High%20Availability/Untitled.png](3%20High%20Availability/Untitled.png)

- E.x: I have 3 of my phone operators in the first building in New York and maybe I'll have 3 of my phone operators in the second building on the other side of the United States, in San Francisco.

    Now, if my building in New York loses their Internet connection or their call connection, then that's okay, they can't work but my second building in San Francisco is still fine and they can still take the phone calls.

    → So, in that case, my call center is highly available.

- The high availability can be passive (for RDS Multi AZ for example)
- The high availability can be active (for horizontal scaling)