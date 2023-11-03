---
tags:
  - Architecture
---
# Vertical Slice Architecture

Vertical slice architecture is based around the principle _"things that change together should be near each other"_. It applies the **_Single Responsibility Principle (SRP)_** and **_Open-Closed Principle (OCP)_** which leads to a very **high cohesion**.
Code changes (add, remove, change) often have impact on one (main) slice and helps to guarantee that nothing else breaks.

Vertical slice architecture can be combine with other architectures like Layered or [Onion](onion.md) and works very well with the [Lightweight Architecture](lightweight.md) by applying those architectures within a single slice.

In other architectures we often see the problem that single entities such as a XYService grows to immense size but in the end a GetXY endpoint only relies on the GetXY method of the service which only relies on the GetXY method of the repository and so on. A single change on the repository then leads to an indirect change on all XY features (since XYRepository change -> XYService change -> XYControllers change) and therefore to possible bug in all parts of that feature.

Works well together with a "task based UI"