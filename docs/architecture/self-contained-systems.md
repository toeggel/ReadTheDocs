---
tags:
  - Architecture
aliases:
  - self-contained systems
  - scs
---

# Self-contained Systems (SCS)

An architectural approach that separates a larger system’s functionality into many independent, collaborating systems. This approach helps avoid the problem of large monoliths that grow constantly and eventually become unmaintainable

**Key characteristics of SCS:**
- **Autonomous:** Each SCS is an autonomous web application (DB, Backend, Frontend, ...)
- **One Team Ownership:** Each SCS is owned by one team and a user story is typically implemented by one team changing one SCS, promoting developer productivity and minimizing coordination efforts
- **Single SCS Deployments**: SCS should ensure that a feature can be implemented in a single SCS, allowing it to be brought into production with a single deployment. This differs from microservices, which may require changes to multiple microservices for a single feature.
- **Asynchronous Dependencies:** Communication with other SCSs or third-party systems is asynchronous wherever possible
- **No Shared Business Logic:** To avoid tight coupling, an SCS should share no business code with other SCSs
- **Hardly Shared Infrastructure:** Shared infrastructure should be reduced to increase availability and decrease coupling

While SCS are similar to microservices, there are differences. A system will usually contain fewer SCS than microservices. Also, microservices can communicate with other microservices – even synchronously. SCS prefer no communication or asynchronous communication. A SCS has the size of at least one microservice.


# Related

[vertical-slice](vertical-slice.md)