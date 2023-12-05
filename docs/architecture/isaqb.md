---
tags:
  - Architecture
  - Architect
---

# iSAQB

## Architekturziele

Architekturziele => Langfristige ziele

Projektziele => kurzfristige Ziele

Als Architekt muss ich versuchen eine möglichst grosse Schnittmenge zwischen Architekturzielen und Projektzielen zu erreichen.

Ziele explizit machen und festhalten (dokumentieren)

> ❌ Architektur per Zufall ist keine Architektur

## Rolle: Architekt

* Ausserhalb vom Team (Elfenbein) -> aka. **AaaS** (Architect as as Service)
	* usually bad because there is no feedback loop
* Das ganze Team
* Gewisse Personen im Team übernehmen gewiss Architektur Aufgaben
* Verteilte Architektur. Architekten sind im Team

## Bausteine

 * Kapseln Verhalten
 * definieren Schnittstellen
 * wiederverwendbar
 * austauschbar

## (Qualitäts-) Anforderungen

* Funktionale Anforderungen (Grund für QA)
* Randbedingungen (Grund für QA)
* **Qualitätsanforderungen** (QA) (früher Nicht-funktionale-Anforderungen) (alternative: *architecture characteristics*)
    * Kernaufgabe als Architekt
* Qualitätsszenario (Zur Verifizierung oder Bewertung von QA)
    * Testfälle für Software Architektur (oft nicht automatisch/trivial ausführbar)
* Qualitätsmerkmale (kategorisieren QA)
    * Benutzbarkeit, Performance, *abilities, ...
* Nicht-Anforderungen (not in scope) => super wichtig

Often it is impossible to prioritize the architecture characteristics (with the stakeholders). Instead we should identify the 3 most important ones (but unprioritized).

### Qualitätsszenario

* Testen unsere Qualitätsanforderungen
* Kann die Architektur mit den neuen Anforderungen umgehen?
* Kommen beim Architekturbrezel zum Einsatz

Verschiedene Szenarien:

* Verwendungsszenarien
    * Normales arbeiten am System
* Änderungsszenarien
    * Änderung am System
    * z.B.: "Anbindung eines neue Payment Provider darf nicht mehr als 10'000 CHF kosten." Dies ist **kein** Qualitätsszenario für die Architektur, weil ich dies mit der Architektur nicht erreichen kann (zu viel andere Faktoren spielen eine Rolle). Besser wäre: "Anbindung eines neue Payment Provider darf nicht mehr als den Payment-Baustein betreffen". Dies kann die Architektur ermöglichen *und* hat auch Einfluss auf die Kosten.
* Stressszenarien
    * Etwas unerwartetes passiert mit dem System

> [!TIP] Es ist schwierig Qualitätsszenarien zu finden, welche ich (als Architekt) mit der Architektur beeinflussen kann.

Beschreibung von Qualitätsszenario (Basierend auf Qualitätsanforderungen)

* Qualitätsattribut
    * *Performance*
* Umgebung - Gerät, Location, last des Systems
    * *Normalbetrieb*
* Quelle - Auslöser, Trigger
    * *Reisender*
* Artefakt
    * *über Mobile App*
* Reaktion
    * *liefert gefundene Reisemöglichkeit*
* Messen - Muss nicht eine Zahl sein. Kann die Architektur damit umgehen?
    * *innerhalb 5sec*

### Kohäsion von Anforderungen

Clustering von Anforderungen (Funktionales Clustering / Fachlicher Schnitt) nach unterschiedlichen Kriterien. Z.B.:

* Prozesse / Abläufe (Funktionalität)
* Daten
* Rollen (wer arbeitet mit der Software)
  
> [!INFO] Betrachte Architektur in erster Linie aus funktionaler Sicht (Business Sicht). Das Business entscheidet ob die Architektur gut ist.

## Sichten

### Kontexsicht / Kontextabgrenzung

>[!INFO] Kein Projekt ohne fachlichen Kontext

* Erste Ebene ist oft sinnvoll aus fachlicher Sicht darzustellen
    * Datenfluss aus fachlicher Sicht (Abhängigkeit interessiert das Fach oft nicht).
    * Sind Teile des Systems instabil? => Das Fach muss da Antworten haben
    * Wo sind Risiken? (z.B.: Dimensions erlaubt nur 30 Request/min) => markiere diese
    * Ähnliche Nachbarsysteme => Fachliche Cluster bilden
* Technische Kontext Sicht ist oft nicht notwendig.

### Bausteinsicht

* Verschiedene Detailstufen
* Wir wollen "fachliche Bausteine"
    * Technische Themen wie z.b. Authorisierung oder Anbindung an Umsysteme (z.B.: Finanzsystem) wollen wir (meistens) nicht als Baustein haben. Ein Adapter/Wrapper o.Ä. kann in diesen Fällen trotzdem technisch gebaut werden um diese zu abstrahieren. Im Diagram können wir diese als "Stereotypen" darstellen

### Laufzeitsicht

* Im Vergleich zu den (meisten) anderen Sichten, sprechen wir hier von Instanzen und nicht von Klassen.
* Sequenzdiagramme können über mehrere Level der Bausteinsicht handeln. So kann Ein Object im Diagramm auf der Kontextsicht liegen (z.b.: ein Umsystem), welches eine Aktion auf Bausteineben 3 aufruft (z.B.: eine speziefische Klasse).

### Verteilungssicht

* Zeigt Software auf Hardware / Infrastruktur
* Unterschiedliche Sichten. Je nach Zielgruppe kann die eine oder andere mehr Sinn ergeben
    * Infrastruktur
        * Was haben wir an Hardware (auch virtuell; z.B. DMZ, VPNs, Server, ...)
    * Deployment
        * Wo wird was deployed? Hier kann z.B. das Frontend sein, welches wir auf einen Server deployen (zur auslieferung an die Clients)
    * Laufzeit
        * Wo läuft *unsere* Software? Hier wäre dann das Frontend beim Client Knoten (z.B. Browser)

## ADR (Architectural Decision Records)

See: [architectural-decision-records](architectural-decision-records.md)

> [!TIP] Entwurfsentscheidungen systematisch dokumentieren

ADRs können auch im selben Repo zum Code eingecheckt werden. So können ADRs bei Diskussionen erstellte werden (z.B.: im Status Proposed) und bei der Implementierung im selben PR wie der Code updated werden. Dadurch werden sie auch gereviewed.

* **Kontext**
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
* **Alternativen** - Lösungsmöglichkeiten
* **Entscheidungen** - Welche Lösung und **warum**!
    * Sind *immutable* aber neue Entscheidungen können diese "überschreiben". Die Dokumentation bleibt. (bzw. ADRs können auch ins Archiv verschoben oder als deprecated markiert werden). Ich möchte gerne die aktuell gültigen ADRs sehen/finden.
* **Konsequenzen** - Positive und negative Folgen
    * Was erlaubt uns nun die Entscheidung? Was verhindert diese?
    * Entscheidungen haben oftmals einen "Haltbarkeitswert" - Sie sollten nach einer gewissen Zeit wieder betrachtet werden.

### Entscheiden

> [!INFO] Nur das nicht Entscheidbare muss entschieden werden.
 
* Vorwärts gehen und (verschiedene Varianten) Ausprobieren.
* Warten und nicht entscheiden ist oft das schlechteste und teuerste.
* Decisions are made in a given context - The same decision made in one context can bring great results, while in another it can cause devastating failure.

## Querschnittliche Konzepte (Cross-Cutting Concerns)

* Lösung für mehrfach auftretenden oder übergreifende Probleme
* Sollen explizit dokumentiert werden (an einem Ort und nicht verteilt)
* Liegen *quer* zu den Bausteinen (und sind keine fachliche Bausteine) können aber als Bausteine behandelt werden.
* Werden nicht aus fachlicher Motivation getrieben
* Sind wiederverwendbar

## Dokumentation

> [!INFO] Muss angemessen und Stakeholdergerecht sein

Warum schreiben ich Doku?

* Transparent
* Explizit
* Konsistenz (als Kommunikationsgrundlage)

Angemessen

* Kontext und Zielgruppen abhängig

Korrektheit

* Lieber korrekt als vollständig
* Aktuell
* Verifizieren

Wartbarkeit

* Anpassbar
* Navigierbar

Verständlichkeit

* Zielgruppen abhängig

Inkrementell

### How-to

* Top-Down
* Text & Bild
* Template (Standard) e.g. arc42: https://github.com/arc42/arc42-template/tree/master
* Lieber eindeutig (trocken) als *interessant*

## 5 orders of ignorance

* 0th: ich weiss etwas
    * Mein Geburtsdatum
* 1st: ich weiss etwas nicht
    * Ich weiss, dass meine Kollegen ein Geburtsdatum haben, kenne dieses aber nicht. Ich kann sie danach Fragen (weil ich weiss, dass sie eins haben)
* 2nd: unknown unknowns
    * Ich weiss nicht, dass ich etwas nicht kenne
* 3rd: Keine Vorgehensweise Wissenslücken zu schliessen. Ich weiss nicht wie ich an das Wissen kommen kann.
* 4th: Meta nichtwissen (Ich weiss nicht, dass es unterschiedliches Wissen gibt).

Oft bleiben wir bei *1st order of ignorance* hängen. Wir müssen unbedingt auf die 3rd order kommen.

## Schnittstellen

* Einfach zu
    * lernen
    * benutzen
    * erweitern
* Schwer zu missbrauchen
* Vollständig
* Erfüllt Qualitätsanforderungen

**Best Practice**

* Die Gültigkeit (Dauer, LTS) einer Schnittstelle (Spezifische Version) soll möglichst gleich mit der Veröffentlichung der Schnittstelle  publiziert/kommuniziert werden. (Api V1.0 ist bis 31.08.23 gültig). Die Gültigkeit kann später "einfach" verlängert werden.

## Architekturbewertung


> [!INFO]  Erfüllt die Architektur die Qualitätsziele (Qualitätsanforderungen) die an sie gestellt werden.

Quantitative Bewertung

* Messbare Werte (Zahlen). z.B.: Metriken
* ⚠ Wichtig: Metriken über die Zeit betrachten
* Geben oft hinweise, wo ich eine qualitative Bewertung machen soll => "Das schaue ich mir mal genauer an"

Qualitive Bewertung

* Soll-/Ist-Analyse (nicht inhaltlich/funktional sonder auf die Architektur bezogen)
* Ohne Qualitätsanforderungen kann ich dies nicht wirklich beurteilen.
* Szenario-basierte Architekturanalyse => Architecture Tradeoff Analysis Method (ATAM) => ZAAF (ATAM von Zühlke)
    * Qualitätsszenario anschauen und bewerten ob unsere Architektur dies unterstützt