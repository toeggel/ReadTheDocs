---
tags:
  - dotNet
---
# Record types

Can your data type be a _value_ type? Go with `struct`. No? Does your type describe a value-like, preferably immutable state and is used in unidirectional (one way) flow? Go with `record`.

Use `class` otherwise. So...

1.  Yes, use `record`s for your DTOs if it is one way flow.
2.  Yes, immutable request bindings are an ideal user case for a `record`

```cs
public record MyDto(string FirstName, string LastName) : IMyBase;
```

