# Lightweight with vertical slices

## Lightweight API
The lightweight API is an approach to building APIs without complex architectural patterns. The lightweight API contains just the essential components needed to build an HTTP API, and to provide CRUD operations. The approach is used for prototyping, rapid application development, or microservices. “Lightweight” frameworks such as Node JS, Java Spring Boot, or Python Flask improve development efficiency even further. ASP.NET Core 6 now provides language constructs to create lightweight APIs as well (Minimal Api).

* ✅ Reduces boilerplate to a minimum.
    * No need to write code (classes, services, commands, ...) just to fulfil [architecture](architecture.md).
* ✅ Simple cases can be implemented simple. Complex cases are possible.
    * We don't have an architecture which is built around (few) complex cases and making therefore the simple cases difficult as well but rather build it around simple cases and keep the possibility to implement complex cases.
* ✅ Easier testing 
    * Less layers, less classes, simpler dependency injection.
* ❌ Solution might struggle with cross-cutting concerns and complex business logic / requirements.

## Feature driven (vertical slice)
The system is structured around features and built along vertical slices, encapsulating and grouping all concerns together (request handling, business logic, DB access, ...). Each slice is isolated from each other slice. Some shared services might exist to handle more complex logic which can be reused among multiple slices.

* ✅ Very high cohesion and low coupling.
    * Everything that changes together is grouped together.
    * Fewer side effects.
    * Lower chance of breaking code during refactorings.
* ✅ Code is mainly added rather than changed.
    * Lower chance of breaking code during development.
* ❌ Code reuse is more difficult to handle (duplication means… duplications, sharing means coupling).

## Design
The API is designed around individual endpoint classes. Each one has a single purpose and endpoint.

These __core principles__ outline the design:

* The code for each feature (vertical slice) lies within its own namespace (or feature folder).
* An endpoint has a single purpose.
* A controller has a single endpoint (controller can be grouped with the TagsAttribute).
* Only GET endpoints have a DTO as response, all other endpoints return a status code only.
* The frontend must retrieve new/updated data after the create/update operation.
* There is no layering - business logic and data access reside in the controller/namespace.
* We use ad-hoc decomposition within the controller namespace.
* Shared code resides in services.
* Endpoints are unit tested.

💡 __Notes:__

* We do not use the Minimal API language features of .NET 6 since we currently do not see a big benefit in using it.
* Unlike microservices, our endpoints access/edit a single data model without being limited to a specific data space.
 *Since we are reusing the same model throughout the solution, we use DTOs instead of returning entities.

## Reasoning
Some drawbacks were identified for an onion architecture, particularly in the area of the architectures complexity in relation to fairly simplistic business requirements. A lot of “boilerplate” needs to be written just to satisfy the architectures need whereas the actual business logic often get lost in its depth.

A layered architecture is considered as an easier alternative to the onion architecture but also to similar for an actual and relevant improvement of the drawback.

If we can expect that most requirements will be rather simple and mostly CRUD-like, we can go with a somewhat more minimalistic approach where we try to optimize the architecture around those simple use cases instead of the few complex ones. This should result in a straightforward implementation for the majority of use cases but still allows the implementation of more complex use cases.  

By following this simpler approach from the start, we ensure that the code is only as complex as it needs to be.

Open Points
* ❌ Uncertain on how it performs for more complex cases / business logic.
* ❓ Can we still bring in a good structure and guidelines to have uniformed code?
* ❓ What do we do with complex business logic?
* ❓ Can (should) we abstract 3rd party libraries (to not have every piece of code be dependent on every SDK or library)


### Is SOLID
1. Single-Responsibility Principle
* Each class has a single responsibility (because of verticle slice).

2. Open-Closed Principle
* It is open for extensions (create new classes).
* Adding a new slice does not need modification of existing code => It is closed for modifications.

3. Liskov Substitution Principle
The subclasses should be substitutable for the base classes.

4. Interface Segregation Principle
All user interfaces should be separate from each other. Also, it is a good practice to have many intent-driven interfaces over one general-purpose interface.

5. Dependency Inversion Principle
The modules should depend on the interfaces or the abstract classes and not the concrete classes and functions.