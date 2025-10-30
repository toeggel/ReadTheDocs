---
tags:
  - Architecture
---

# Onion

The Onion Architecture fosters a modular and maintainable design by enforcing a strict separation of concerns and promoting dependency inversion. It enables the creation of applications that are flexible, testable, and scalable over time. It organizes an application into concentric layers towards the core that represents the domain. The further in, the less changes should occur (the domain my life longer than the application).
It separates the application's core business logic and external concerns, such as database access, UI, and frameworks. 

It is similar to the classic n-tier layer architecture but more complex. All the folders are now projects, whenever something is change you go through all projects and all folder. Navigation becomes a nightmare.

> Also known as the vegetable architecture - you know, the kind that makes you cry when you look at it.

As with other layered architectures, the focus is on the **separation of technical** concerns.

# Related

[domain-centric-architecture](domain-centric-architecture.md)
[hexagonal-architecture](hexagonal-architecture.md)