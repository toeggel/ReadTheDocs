---
tags:
  - Architecture
---

# Domain Centric Architectures
Examples are [Onion](onion.md), [Hexagonal](hexagonal-architecture.md), Ports and Adapter and Clean architecture.

Domain-centric (or domain-driven) architectures place the business domain - its concepts, rules, and language - at the core of the software design. Rather than starting from technical layers (UI, database, etc.), development revolves around domain models that capture the essential business logic.

**Key Ideas:**

- **Domain as the Core:** The domain model is the "source of truth"” and all other layers (UI, persistence, infrastructure) serve it.
- **Ubiquitous Language:** Developers and domain experts share a consistent vocabulary embedded in the model itself.
- **Bounded Contexts:** Complex domains are divided into smaller, coherent areas, each with its own model and rules.  
- **Layered Design:** Often follows a structure like Domain → Application → Infrastructure → Interface or similar.
- **Strategic Integration:** Context maps define how different bounded contexts interact - through APIs, events, or shared kernels.

## When to use a Domain Centric Architecture

> With domain centric architectures we try to reduce the blast radius of volatile external dependencies.

When we have (lots of) (volatile) external dependencies that are used within (many places in) our applicaiton.
