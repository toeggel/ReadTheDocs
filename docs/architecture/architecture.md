---
tags:
  - Architecture
---

# Architecture

Eine Architektur braucht eine Vision (und ist auf das Business fokussiert).

Sie richtet sich an Werten (von Stakeholdern) aus. Steht Time-to-market im Vordergrund, wird der Fokus auf eine gute Entwicklungsproduktivität gelegt.

Know __whether__ to use a tool or technology (and only partially how)

>[!QUOTE] Architecture is the art of choosing the right trade-offs

> [!TIP]
> Don’t try to find the _best_ design in software architecture; instead, strive for the _least worst_ combination of trade-offs.

**What is architecture**

* Structure
* Split into components
* Interfaces
* Dependencies 

## Goal

* Technical decisions to deliver features efficient and effective - and close the feedback loop fast
* Most simple (_and not most flexible_) solution for the problem to solve
* Keep the cost of change low

See: [Architekturziele](isaqb.md#Architekturziele)

## Architectural Drivers

Architectural Drivers are usually connected with each other and have trade-offs.

- **Functional Requirements** - what and how problems does the system solve
- **Quality Attributes** - a set of attributes that determine the quality of architecture like maintainability or scalability.
- **Technical Constraints** - technology standards, tools limitations, team experience
- **Business Constraints** - budget, hard deadline

> _You have some service that calculates some important thing (Functional Requirement) in 3 seconds (Quality Attribute - performance). A new requirement appears, calculation is more complex and takes now 5 seconds (Performance decreased). To go back to 3 seconds another technology could be used, but there is no time for it (Business Constraint - hard deadline) and nobody has used it in the company yet (Technical Constraint - team experience). The only option to increase performance is to move the calculation to the stored procedure, which decreases maintainability and readability (Quality Attributes)._

## Architecture Smoketest (based on documentation)

* What are the principles or decisions of the solution? Why?
* What are the responsibilities of each box and line in a diagram?
* How does the Architecture fulfill the systems quality requirements?

### Fitness tests

Fitness functions validate architecture characteristics, not domain criteria; unit tests are the opposite. Thus, an architect can decide whether a fitness function or unit test is needed by asking the question: “Is any domain knowledge required to execute this test?” If the answer is “yes,” then a unit/function/user acceptance test is appropriate; if “no,” then a fitness function is needed.

**Example:**  A tests which makes sure that certain module dependencies are enforced (Module X does not reference Module Y). 

## Grundsätze, Prinzipien
### Grundsätze (always true)

* Success of the architecture is meassurd by the stakeholders (not by the architect)
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

> [!INFO] Viele Architekturentscheide können __aufgeschoben__, und __lokal__ anstatt __zentral__ getätigt werden.

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

# Finding an architecture

- there are no stupid ideas,
- we don’t criticize; we focus on our ideas, not other people’s,
- we generate as many ideas as possible,
- when we run out of ideas, we should still try to grind a bit longer and tell ourselves to generate 2-3 more. It’s like running; often, the best results occur when we pass the first fatigue threshold,
- however, it is important to set a maximum duration for brainstorming. It should be an intensive and productive meeting. There’s no point in making it an endless one. You can always organize several sessions.

# Best Practices

- Modularity
- KISS
- Separation of Concerns
- Release fast, release often 
	- "If you do a big bang rewrite, the only thing you're certain of is  a big bang" 💥
	- "You cannot become a Kung-Fu master by reading about Kung-Fu. You have to practice it"