---
tags:
  - Architecture
---

# Monolith

A **modular monolith** has many overlapping advantages with [microservices](microservice.md). However, in a monolith architecture it is a lot easier to bypass de modularity and therefore creating a big ball of mud. One way to enforce the modularity is by writing architectural [fitness functions](architecture.md#Fitness%20tests).

Monolith and microservices should not be on a black-white scale but rather on a continuous scale. If we have a modular monolith we can extract specific modules into services for optimization or because they have specific needs (such as individual deployable).

## Concerns

- Long compilation times.
- Long-running test.
- Deployment to production takes a long time.
	- Single deployment unit.
- Limited language agnosticism.
- Centralized development.

### Modular

The module’s independence is determined by three main factors:

- number of dependencies (to other modules) - could be reduced e.g. with a *mediator*
- strength of dependencies (how chatty is the module with another one) - should these modules be *merged*?
- stability of the modules on which the module depends on (how many modules need a change when I change my module?) - *merge*?

Technical layers are often used as "modules" but this is very bad in regards to "stability" since a new feature usually needs a change in all modules (UI, API, Business, DB). [Vertical Slice](vertical-slice.md) seems more reasonable.

Module must have **well-defined interface** (a contract). We only want to have one "arrow" from Module A -> Module B.

---

[microservice](microservice.md)