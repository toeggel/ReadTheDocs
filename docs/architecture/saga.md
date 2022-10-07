# Saga Pattern
A saga is a sequence of local transactions over multiple separated services. In case of an error, undo operations need to be performed.

## Problem:
"Database per service Pattern" is applied, distributed transactions are not an option but we need to implement a transaction which spans over multiple services.

## Solution
Each service updates it DB locally and publishes a message to trigger a next local transaction. If one transaction fails it violates the business rules and saga needs to execute compensating transactions (undo) for already applied changes.