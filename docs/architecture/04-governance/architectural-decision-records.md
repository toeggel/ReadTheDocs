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

## Template Example

See: 
- [adr-1-template](../07-examples/adr-1-template.md)
- [adr-2-template](../07-examples/adr-2-template.md)

##  ADR Example
### Use Markdown Architectural Decision Records

#### Context and Problem Statement

We want to record architectural decisions made in this project independent whether decisions concern the architecture ("architectural decision record"), the code, or other fields.
Which format and structure should these records follow?

#### Considered Options

* [MADR](https://adr.github.io/madr/) 4.0.0 – The Markdown Architectural Decision Records
* [Michael Nygard's template](http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions) – The first incarnation of the term "ADR"
* [Sustainable Architectural Decisions](https://www.infoq.com/articles/sustainable-architectural-design-decisions) – The Y-Statements
* Other templates listed at <https://github.com/joelparkerhenderson/architecture_decision_record>
* Formless – No conventions for file format and structure

#### Decision Outcome

Chosen option: "MADR 4.0.0", because

* Implicit assumptions should be made explicit.
  Design documentation is important to enable people understanding the decisions later on.
  See also ["A rational design process: How and why to fake it"](https://doi.org/10.1109/TSE.1986.6312940).
* MADR allows for structured capturing of any decision.
* The MADR format is lean and fits our development style.
* The MADR structure is comprehensible and facilitates usage & maintenance.
* The MADR project is vivid.
# Related
- [architecture-documentation](architecture-documentation.md)