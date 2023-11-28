---
tags:
  - Architecture
  - Pattern
---

# Patterns

## Strangler (Fig) Pattern
Incrementally migrate a legacy system by gradually replacing specific pieces of functionality with new applications and services. As features from the legacy system are replaced, the new system eventually replaces all of the old system's features, strangling the old system and allowing you to decommission it.

> [!TIP] Use this pattern when gradually migrating a back-end application to a new architecture.

## Anti-Corruption Layer
Legacy systems often suffer from quality issues such as convoluted data schemas or obsolete APIs. A Facade helps to keep the interface of a new Application clean. 

> [!TIP] Use this pattern to ensure that an application's design is not limited by dependencies on outside subsystems.

## Design patterns for microservices
![microservices-patterns](../assets/microservices-patterns.png "Design patterns for microservices")
Microsoft ["Design patterns for microservices"](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/patterns)

## Saga Pattern

A saga is a sequence of local transactions over multiple separated services. In case of an error, undo operations need to be performed.

### Problem

"Database per service Pattern" is applied, distributed transactions are not an option but we need to implement a transaction which spans over multiple services.

### Solution

Each service updates it DB locally and publishes a message to trigger a next local transaction. If one transaction fails it violates the business rules and saga needs to execute compensating transactions (undo) for already applied changes.

## CQRS Pattern

**C**ommand and **Q**uery **R**esponsibility **S**egregation is a pattern that separates read and write operations for a data store. This allows us to optimize both acts.

> [!INFO] *read* and *write* operation should somehow be *separated*.

### Problem

Read and write workloads are often asymmetrical, with very different performance and scale requirements.
We often try to balance between reads and writes and can never optimize for both. 

* Mismatch between the read and write representations of the data
* The traditional approach can have a negative effect on performance due to load on the data store and data access layer, and the complexity of queries required to retrieve information.
* Managing security and permissions can become complex, because each entity is subject to both read and write operations, which might expose data in the wrong context.

### Solution

CQRS separates reads and writes into different models, using **commands** to update data, and **queries** to read data.

- Commands should be task-based, rather than data centric. ("Book hotel room", not "set ReservationStatus to Reserved").
- Commands may be placed on a queue for asynchronous processing, rather than being processed synchronously.
- Queries never modify the database. A query returns a DTO that does not encapsulate any domain knowledge.
- DB might somehow be separated (e.g. DB, tables, views) for the specific (performance) needs (write vs. read).
- Consider materialized views for the queries.

CQRS can provide limitless scalability for both the read and write side but with some trade-offs, like eventual consistency, which need to be clearly communicated to the business user.

> [!TIP] Use when we have rich/complex business.

MediatR is **not** needed to implement CQRS! It doesn't even do a good job in *actually* separating Commands and Queries (This is done by conventions and guidelines). 

## Outbox Pattern
### Problem

How to reliably/atomically update the database and send messages/events?

### Forces

* 2PC (two phase commit) is not an option
* If the database transaction commits messages must be sent. Conversely, if the database rolls back, the messages must not be sent
* Messages must be sent to the message broker in the order they were sent by the service. This ordering must be preserved across multiple service instances that update the same aggregate.

### Solution

A service that uses a relational database inserts messages/events into an _outbox_ table (e.g. `MESSAGE`) as part of the local transaction (i.e. while performing the actual DB transaction like creating an order). Both, the message and the entity are committed (or rollbacked) with the same commit.
A separate _Message Relay_ process publishes the events inserted into database outbox table to a message broker.

### Alternatives

https://stackoverflow.com/questions/72284628/comparing-cdc-vs-outbox-pattern-for-creating-event-streams

See also: 
[Saga Pattern](patterns.md#Saga%20Pattern)

* https://github.com/meysamhadeli/awesome-dotnet-tips