---
title: Obsidian
tags:
  - obsidian
  - PKM
---
# Obsidian
On this page I test Obsidian features. Some might work, some wont. Above this title we have some font matter properties

## Inline

![misc](misc.md)

## Links

[misc](misc.md)
[ngrx-push](../frontend/js/ngrx-push.md)

## Callout

> [!info]
> some callout


> [!tip] Just Another Callout
> Wow

## PlantUML

```plantuml
@startuml C4_Elements
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

Person(personAlias, "Label", "Optional Description")
Container(containerAlias, "Label", "Technology", "Optional Description")
System(systemAlias, "Label", "Optional Description")

Rel(personAlias, containerAlias, "Label", "Optional Technology")
@enduml
```

## Draw.io Plugin

Within table

| sketchy style | non-sketchy style |
| - | - |
|   ![](../assets/diagram-test.svg)  |  ![diagram-test-2](../assets/diagram-test-2.svg)|

## Tags

#PKM #obsidian 