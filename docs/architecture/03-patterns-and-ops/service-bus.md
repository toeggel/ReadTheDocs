---
tags:
  - Distributed-System
---

# Service Bus Messaging 

## Queue

> [!TIP] Use when there is a need to pass the message in the one-to-one system. 

Messages in queues are ordered and timestamped on arrival.


![service-bus-queue](../assets/about-service-bus-queue.png "service-bus-queue")
 
## Topic

 > [!TIP] Use when there is a need to send the message to multiple systems.

Topics can have multiple, independent subscriptions, which attach to the topic and otherwise work exactly like queues from the receiver side.

![service-bus-queue](../assets/about-service-bus-topic.png "service-bus-queue")