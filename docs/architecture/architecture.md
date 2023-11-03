---
tags:
  - Architecture
---
# Architecture

> Architecture is the art of choosing the right trade-offs

> The life of a software architect is a long (and sometimes painful) succession of sub-optimal decisions made partly in the dark.

> Eine Architektur braucht eine Vision (und ist auf das Business fokussiert).

Sie richtet sich an Werten (von Stakeholdern) aus. Steht Time-to-market im Vordergrund, wird der Fokus auf eine gute Entwicklungsproduktivität gelegt.

Know __whether__ to use a tool or technology (and only partially how)

## Goal

* Technical decisions to deliver features efficient and effective - and close the feedback loop fast
* Most simple (_and not most flexible_) solution for the problem to solve
* Keep the cost of change low

## What is architecture

* Structure
* Split into components
* Interfaces
* Dependencies 

## Architecture Smoketest (based on documentation)

* What are the principles or decisions of the solution? Why?
* What are the responsibilities of each box and line in a diagram?
* How does the Architecture fulfill the systems quality requirements?

## Grundsätze, Prinzipien
### Grundsätze (always true)

* Success of the architecture is meassured by the stakeholders (not by the architect)
* KISS
* "There is no silver bullet". Always decide specifically
* Make everything explizit (requirements, assumptions, non-functional requirements)
* Expect changes. "Change is gooood"
* Expect errors
* Keep non-functional requirements (quality attributes) in the mind all the time

### Prinzipien (etablierte Regeln)

* loose coupling
    * Reduce dependencies (everywhere not just code)
* high cohesion

# Emergent Architecture
Emergent Architecture basiert auf einem stabilen __Kern__

> [!info] Viele Architekturentscheide können __aufgeschoben__, und __lokal__ anstatt __zentral__ getätigt werden.

Gewisse Entscheide müssen früh getroffen werden:

* Wie soll das System aussehen (__Übersicht__, __Vision__)
* Wo sind die Hauptabstraktionen
* Wie soll das Projektteam/System strukturiert sein (Conway’s Law)

Der __Kern__ der Emergenten Architektur soll so __stabil__ wie möglich sein. Er wird abgeleitet aus der __Art des Geschäfts__.

Der __Kern__ hat meist __hohe Kosten für Änderung__ oder ihn rückgängig zu machen.

## Architekturentscheide
Faktoren für die Frage __wann__ Architekturentscheide gemacht werden sollen.
* was kostet eine verspätete Entscheidung?
* was kostet es zum Rückgängig machen der Entscheidung?
* werden zukünftige Perspektiven verhindert?
* Ist schnelles Feedback verfügbar?

# Quotes

Story of the Tortoise and the Hare

> Slow and steady wins the race.
> The race is not to the swift, nor the battle to the strong.
> The more haste, the less speed.


Regarding "Cleaning up later"

> Making messes is always slower than staying clean
> The only way to go fast, is to go well.