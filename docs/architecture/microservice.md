---
tags:
  - Architecture
---
# Microservices 

- Do not make long service dependencies (A->B->C->D->...). This will eventually fail (Bad performance and bad availability).
	- This can and has to be solved with data duplication (no changes though)
	- Make a rule that only one hop is allowed A->B 
	- 

# Micro frontend (MFE)

MFE is recommended for teams that require applications to be deployed independently. It is important to consider the cost of MFEs and decide whether it makes sense for your own teams.

With MFE architecture, a large application is split into:

1. A single **Host** application that references external...
2. **Remote** applications, which handle a single domain or feature.

---

[self-contained systems](self-contained-systems.md)
