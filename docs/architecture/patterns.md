---
tags:
  - Architecture
  - Pattern
---
# Patterns

## Strangler (Fig) Pattern
Incrementally migrate a legacy system by gradually replacing specific pieces of functionality with new applications and services. As features from the legacy system are replaced, the new system eventually replaces all of the old system's features, strangling the old system and allowing you to decommission it.

> [!info] Use this pattern when gradually migrating a back-end application to a new architecture.

## Anti-Corruption Layer
Legacy systems often suffer from quality issues such as convoluted data schemas or obsolete APIs. A Facade helps to keep the interface of a new Application clean. 

> [!info] Use this pattern to ensure that an application's design is not limited by dependencies on outside subsystems.

## Design patterns for microservices
![microservices-patterns](../assets/microservices-patterns.png "Design patterns for microservices")
Microsoft ["Design patterns for microservices"](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/patterns)

## Saga Pattern

A saga is a sequence of local transactions over multiple separated services. In case of an error, undo operations need to be performed.

### Problem

"Database per service Pattern" is applied, distributed transactions are not an option but we need to implement a transaction which spans over multiple services.

### Solution

Each service updates it DB locally and publishes a message to trigger a next local transaction. If one transaction fails it violates the business rules and saga needs to execute compensating transactions (undo) for already applied changes.