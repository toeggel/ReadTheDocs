---
tags:
  - Optimization
  - Strategy
  - Pattern
---

# Caching

Different kind of caching exists:
* in-memory caching
* distributed caching
* content caching
* database caching 

## Distributed caching

A distributed cache is a cache shared by multiple app servers, typically maintained as an external service to the app servers that access it.

> **Question:** How can I make sure that the external service is (accessed) fast?

When cached data is distributed, the data:
* Is coherent (consistent) across requests to multiple servers.
* Survives server restarts and app deployments.
* Doesn't use local memory.

.NET Core provides these implementations:
* Distributed Redis cache
* Distributed Memory Cache
* Distributed SQL Server cache
* Distributed NCache cache

**Redis** is an open source in-memory data store.
in-memory --> fast
can be persisted as well

The **in-memory** distributed cache isn't actually a distibuted cache but might be useful if only a single server is used. It allows to easily implement a true distributed cache later.

**SQL Server cache** allows complex queries since it is a relational DB.

> [!info] Redis is generally recommended as a distributed cache solution

