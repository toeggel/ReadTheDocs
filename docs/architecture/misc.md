# Misc

## Distributed Communications Failure

We have 4 option to handle distributed exceptions.
1. Ignore (e.g. Swallow execution)
2. Retry
3. Undo previous steps (could fail as well)
4. Communicator (Two phase commit, distributed transaction (usually doesn't work with web APIs))

For each case and each possible failure (call to XY failed, message to service bus could not be published) we need to consider the 4 options and choose the best.

# Outbox Pattern
## Problem

How to reliably/atomically update the database and send messages/events?

## Forces

* 2PC (two phase commit) is not an option
* If the database transaction commits messages must be sent. Conversely, if the database rolls back, the messages must not be sent
* Messages must be sent to the message broker in the order they were sent by the service. This ordering must be preserved across multiple service instances that update the same aggregate.

## Solution

A service that uses a relational database inserts messages/events into an _outbox_ table (e.g. `MESSAGE`) as part of the local transaction. An service that uses a NoSQL database appends the messages/events to attribute of the record (e.g. document or item) being updated. A separate _Message Relay_ process publishes the events inserted into database to a message broker.

## Alternatives

https://stackoverflow.com/questions/72284628/comparing-cdc-vs-outbox-pattern-for-creating-event-streams

---

[Saga Pattern](patterns.md#Saga%20Pattern)

* https://github.com/meysamhadeli/awesome-dotnet-tips