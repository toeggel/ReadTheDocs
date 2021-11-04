# Architecture
> Eine Architektur braucht eine Vision (und ist auf das Business fokussiert).

Know __whether__ to use a tool or technology (and only partially how)

## Goal
* Technical decisions to deliver features efficient and effective - and close the feedback loop fast
* Most simple (_and not most flexible_) solution for the problem to solve

# Emergent Architecture
Emergent Architecture basiert auf einem stabilen __Kern__
> Viele Architekturentscheide können __aufgeschoben__, ​
und __lokal__ anstatt __zentral__ getätigt warden.​

Gewisse Entscheide müssen früh getroffen werden:​

* Wie soll das System aussehen (__Übersicht__, __Vision__)​
* Wo sind die Hauptabstraktionen​
* Wie soll das Projektteam/System strukturiert sein (Conway’s Law)​

Der __Kern__ der Emergenten Architektur soll so __stabil__ wie möglich sein. Er wird abgeleitet aus der __Art des Geschäfts__.​

Der __Kern__ hat meist __hohe Kosten für Änderung__ oder ihn rückgängig zu machen.

## Architekturentscheide
Faktoren für die Frage __wann__ Architekturentscheide gemacht werden sollen.
* was kostet eine verspätete Entscheidung?
* was kostet es zum Rückgängig machen der Entscheidung?
* werden zukünftige Perspektiven verhindert?
* Ist schnelles Feedback verfügbar?

# Patterns
## Strangler (Fig) Pattern
Incrementally migrate a legacy system by gradually replacing specific pieces of functionality with new applications and services. As features from the legacy system are replaced, the new system eventually replaces all of the old system's features, strangling the old system and allowing you to decommission it.

> 💡 Use this pattern when gradually migrating a back-end application to a new architecture.

## Anti-Corruption Layer
Legacy systems often suffer from quality issues such as convoluted data schemas or obsolete APIs. A Facade helps to keep the interface of a new Application clean. 

> 💡 Use this pattern to ensure that an application's design is not limited by dependencies on outside subsystems.
