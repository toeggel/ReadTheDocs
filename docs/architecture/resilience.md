---
tags:
  - Resilience
  - Strategy
  - Distributed-System
  - Quality-Attribute
  - Pattern
---

# Resilient

Consider: [Polly](tools.md#Resilience)

## Retry

> [!ABSTRACT] The Retry pattern enables an application to retry an operation in the expectation that it’ll succeed. 

See also: Exponential BackOff
## Circuit Breaker

> [!ABSTRACT] The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.

Circuit Breaker is used to detect failures and prevent a failure from constantly recurring. The pattern helps to prevent catastrophic cascading failure across multiple systems. 
If an error occurs in a call to another service, we don't want to spam that service with additional request. If we expect it to fail we instead return an error or some kind of result without even calling the service.
It is therefore often built on top of the [[#Retry]] pattern