# Systematic Composition

1. identify Actors
2. identify Use-Cases
3. identify FR
4. Which are the most difficult non-functional requirements
5. Which are the dominant use-cases

# Functional Requirements

Use-Cases / User Stories

- User Stories besser für kleinere Projekte
- Use-Cases oder Epics für grössere

Alle use-cases erfassen, besonders wichtig für die Frage *"Was ist in Scope und was nicht?"*.
Umsysteme identifizieren.

# Non-Functional Requirements

The Big 4

- Performance
- Availability
- Operability
- Maintainability

Make the number graspable / concrete (important: maximum). Important Quality Attribute

- How many? 1000?
- How many per time frame? 280 events / seconds?

# Dominant Use-Cases (UC)

- Usually have the hardest performance or availability requirements.
- The things I'm afraid of or I don't know or understand
- Pain points of the previous systems

-

- Which are the complex use-cases?
- Which are the use-cases with high throughput?

# Define the architecture

Follow the dominant UC

- Build sequence diagram and flow based on the UC (step by step) to build the architecture.

Inter-process communication needs a good reason to be introduced! They are expensive and responsible for performance issues.

How to split processes

- Bounded Context
- Types of load (interactive, batch)
- Availability
- Need for different integration technologies
- Performances
- Capacity

# Evaluate Architecture

## Anchor the design to reality

- PoC
- Spike
- Baseline
- Properties of a Product (fact, limits, numbers)

## Compare

Define factors I want to evaluate (e.g. throughput where we require at least x request per seconds) and place architectures (variants) on that graph.

throughput
low | --A--R-----B---| high
A: Architecture A
B: Architecture B
R: Required

In this case we can get rid of Architecture A because it does not fulfill the requirement. In other cases we might need to do PoCs or prototyping to figure out where one architectures lie on the scale.

# Select a draft architecture

- Architecture Tipping point
	- One architecture doesn't fulfil the requirements => not viable
- Decision Tipping Points
	- Usually we take the "better" architecture unless it produces immense drawbacks

# Notes

 Wir müssen die kritischen (dominant) Use-Cases betrachten
 
 - 

Risiko basierte Architektur

- Höchstes Risiko zuerst beseitigen

Ich muss die Domäne gut genug verstehen um den Kunden (e.g. BE, BA) zu challenges