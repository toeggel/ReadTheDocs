---
tags:
  - Architecture
  - Documentation
---

# Architectural Decision Records (ADR)

> [!TIP] Entwurfsentscheidungen systematisch dokumentieren

ADRs können auch im selben Repo zum Code eingecheckt werden. So können ADRs bei Diskussionen erstellte werden (z.B.: im Status Proposed) und bei der Implementierung im selben PR wie der Code updated werden. Dadurch werden sie auch gereviewed.

**Kontext**

* Fragestellung - Warum und Wozu?
* Einflüsse - Wer, Was, Wie beeinflusst die Entscheidung?
	* Stakeholder, Randbedingungen, Qualitätsanforderungen
* Kriterien - Bewertungsmassstäbe
	* Pro, Cons ist oft nicht gut, weil sie schon oft *biased* sind
	* Nach was will ich überhaupt bewerten?
		* Danach schreibe ich nicht auf was pros/cons sind sondern welche Entscheidung erfüllt die Kriterien (am besten)
	* Beispiele:
		* Kosten
		* Teamerfahrung
		* Teamskalierbarkeit
		* Softwareskalierbarkeit
		* Komplexität
		* Testbarkeit

**Alternativen** - Lösungsmöglichkeiten
**Entscheidungen** - Welche Lösung und **warum**!

* Sind *immutable* aber neue Entscheidungen können diese "überschreiben". Die Dokumentation bleibt. (bzw. ADRs können auch ins Archiv verschoben oder als deprecated markiert werden). Ich möchte gerne die aktuell gültigen ADRs sehen/finden.

**Konsequenzen** - Positive und negative Folgen

* Was erlaubt uns nun die Entscheidung? Was verhindert diese?
* Entscheidungen haben oftmals einen "Haltbarkeitswert" - Sie sollten nach einer gewissen Zeit wieder betrachtet werden.

## Template

### Title

\[date]
\[status]

_ADR: A short noun phrase containing the architecture decision_

_Context_  
In this section of the ADR we will add a short one- or two-sentence description of the problem, and list the alternative solutions. 
The issue motivating this decision, and any context that influences or constrains the decision. 

_Decision_  
In this section we will state the architecture decision and provide a detailed justification of the decision. 
The change that we're proposing or have agreed to implement."

_Consequences_  
In this section of the ADR we will describe any consequences after the decision is applied, and also discuss the trade-offs that were considered.
What becomes easier or more difficult to do and any risks introduced by the change that will need to be mitigated.
# Related
- [architecture-documentation](architecture-documentation.md)