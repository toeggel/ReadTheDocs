---
tags:
  - Architecture
---

# Vertical Slice Architecture

aka VSA

> [!ABSTRACT] Organise by use case, not technical responsibility.

> [!ABSTRACT] Minimize coupling between slices, and maximize coupling in a slice.

Vertical slice architecture is based around the principle _"things that change together should be near each other"_. It applies the **_Single Responsibility Principle (SRP)_** and **_Open-Closed Principle (OCP)_** which leads to a very **high cohesion**.
Code changes (add, remove, change) often have impact on one (main) slice and helps to guarantee that nothing else breaks.

- Vertical slice architecture can be combine with other architectures like Layered or [Onion](onion.md) and works very well with the [Lightweight Architecture](lightweight.md) by applying those architectures within a single slice.
	- Different slices may implement different architectural flavors. 
- Works well together with a "task based UI"
- Vertical slice architecture has some similarities to [CQRS](patterns.md#CQRS%20Pattern).
- CQRS is a good pattern to use within VSA (Why? How?)

Consider to take the vertical slice up to the UI. On one view there is one query request performed. The result of the query has all the data necessary for that view. The query should therefore not return an entity but a specific model. In this case, inner classes can be useful.

```csharp
public class Person
{
	public int Id { get; set; }
	public string FirstName { get; set; }
	public string LastName { get; set; }
	public List<Order> Orders { get; set; }

	public class Order {
		public int Id { get; set; }
		public string Title { get; set; }
		public string Description { get; set; }
	}
}
```

A command can be a response of a query. We see this a lot for edit forms where we first request the data (command) and send the same data back after editing

```csharp
public class Edit { 
	public class Query : IRequest<Command> { 
		public int? Id { get; set; } 
	} 

	public class Command : IRequest { 
		public int Id { get; set; }
		public string LastName { get; set; }
		public string FirstMidName { get; set; }
		public DateTime? EnrollmentDate { get; set; } 
	}
}
```

## Sharing Code

Often the question arise about how code can be shared in a VSA. There are multiple approaches to it.
First of all we need to ask us *why* we want to share code before we answer the *how*.
**Why:**
- **Cross-cutting-concern:** Have a module for it.
- **Core concern:** Have a module for it.
- **Domain concern:** Consider creating a domain module for it. This might slightly break the VSA principles but makes use of domain centric architecture ideologies.
- **Others:** Consider duplication.

## Comparison to other architectures

In other architectures we often see the problem that services for single entities such as a XYService grows to immense size but in the end a GetXY endpoint only relies on the GetXY method of the service which only relies on the GetXY method of the repository and so on. A single change on the repository then leads to an indirect change on all XY features (since XYRepository change -> XYService change -> XYControllers change) and therefore to possible bug in all parts of that feature. This reduces the effort for regression tests.

### Layered (incl. Onion, Clean, ...)

Layered architecture (i.e. [Onion](onion.md)) are easy to understand and maintain but impose some rigid constraints on the layers (e.g. which layer can call which other layer). This leads to high coupling inside layers but low coupling between layers. This than leads to more abstractions which means increased complexity. Implementing a feature often leads to making changes in many different layers => low cohesion. You have to navigate to lots of folders and projects.