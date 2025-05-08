---
title: Obsidian
tags:
  - obsidian
  - PKM
---
# Obsidian

On this page I test Obsidian features. Some might work, some wont. Above this title we have some font matter properties

## Inline

![misc](misc.md#Agile)
## Links

[misc](misc.md)
[ngrx-push](../frontend/js/ngrx-push.md)

## Callout

> [!INFO]
> This callout will get converted to the mkdocs admonition format (see note below) by the mkdocs-callouts plugin

> [!TIP]- Just Another Callout, which is collapsed
> Wow

!!! note
    Callouts (see above) will get converted to this format (mkdocs admonition) by the mkdocs-callouts plugin

**alternative:**

---
>**Tip**
>Just a tip
---


## Formatting

**bold**
*cursive*
==highlight==
~~invalid~~

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

## Mermaid
```mermaid
classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
      +String beakColor
      +swim()
      +quack()
    }
    class Fish{
      -int sizeInFeet
      -canEat()
    }
    class Zebra{
      +bool is_wild
      +run()
    }
```
## Draw.io Plugin

Within table

| sketchy style | non-sketchy style |
| - | - |
|   ![](../assets/diagram-test.svg)  |  ![diagram-test-2](../assets/diagram-test-2.svg)|

## Tags

#PKM #obsidian 