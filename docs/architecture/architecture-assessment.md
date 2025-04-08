---
tags:
  - Architecture
  - Assessment
  - Architect
  - Documentation
---

# Architecture assessment

## Possible Process (as experienced for defining software maturity level)

> [!TIP] Talk with people!
> - Figure out what **exactly** is needed and/or expected. 
> - Where are overlaps with others`?
> - Usually others know the details better. Speak with the people involved (Architects, Devs, QA, RE, PM, PO, ...)

1. Just start somewhere
	- Check any available assessment model: search for *Software quality assessment model*, *Capability Maturity Model Integration (CMMI)*, ISO Standards or similar.
2. Good start is also to check defined (functional) requirements and quality attributes (non-functional requirements).
	- mark what is already there, where is improvement necessary, what is missing (e.g. color code green, orange, red). 
3. Be concrete:
	- What is needed, what do we have. 
	- Compare with known quality standards and quality attributes. 
	- Categorize (Foundation <-> Enterprise, Must-Haves <-> Nice-to-Have, Necessary <-> Optional)
4. What to look for (Ask people about it & check code, repo, pipelines)
	- Are standard components used? Is a standard architecture used?
	- Architecture
	- Type-safety?
	- DB migration
	- CI/CD (automation)
	- Quality (lint, formatting, style guide, structure)
	- Testing
	- Dokumentation
		- ADR
		- SAD
		- User manual
	- Release-management
	- Authorization / Authentication
	- Logging, Monitoring, Observability
	- PR handling
	- More "detailed"/depth
		- Auditing
		- i18n, a11y
		- UX
		- API versioning
		- Licencing
		- Dependency Management / security (see: [Vulnerability monitoring](tools.md#Vulnerability%20monitoring))
5. Report
	- Write everything down that was discussed, decided, identified, 

## Management Report

### Sample table of content

1. Management Summary
2. Über diesen Report
        1. Zielsetzung
        2. Zielgruppe
        3. Autoren
        4. Vorgehen
        5. Abgrenzung
3. Allgemeiner Eindruck
4. Grundlagen
    1. Kein Handlungsbedarf
    2. Handlungsbedarf
        1. Dokumentation
        2. Testfälle
        3. Automatisiertes Testing
        4. Linting
        5. Security Findings
        6. Pipeline
    3. Risiken
        1. Python
5. Enterprise Funktionalität
    1. Kein Handlungsbedarf
    2. Handlungsbedarf aus RFI
        1. Role Based Access Control
        2. i18n (FR 4.7)
        3. Personalisierbarkeit UI (FR 4.4)
        4. Speicherung Nutzungsdaten (NFR 3.5)
        5. Dashboard Systemverantwortliche / Statistik (FR 5.1)
        6. Feedback-Kanal zu UseCase (FR 5.4)
        7. DataPool Import
    3. Handlungsbedarf aus Sicht Enterprise Readyness
        1. Benutzerhandbuch
        2. Accessiblity
        3. User Experience
        4. White Labeling
        5. Dependency Management
        6. License Management
6. Weitere Funktionalität
    4. Handlungsbedarf Backend
        1. MCP
    5. Handlungsbedarf Frontend
        2. Einheitlicher Ansatz im Styling
        3. Dependencies Update
        4. Backend Kommunikation
        5. Cleanup komplexer Codeteile
        6. Data Mode Router
7. Aufwandschätzung
    1. Storypunkte
        1. Grundlagen
        2. Enterprise Funktionalität > RFI
        3. Enterprise Funktionalität > Enterprise Readyness
        4. Weitere Funktionalität
    2. Umrechnungsfaktor
    3. Projekt und Betrieb
    4. Personentage
### Beispiel Text - Management Summary

Der Report bewertet die softwaretechnische Qualität von\[Project] und zeigt Lücken im Vergleich zu den RFI-Anforderungen sowie Erwartungen an eine Enterprise-Applikation auf. Die Analyse basiert auf Gesprächen und einer Quellcode-Sichtung des Frontends.

**Gesamteindruck:** Das Projekt macht einen soliden Eindruck, ist gut strukturiert und setzt zentrale Software-Praktiken ein. Die Architektur folgt etablierten Standards.

**Verbesserungspotenzial:** Es fehlt an vollständiger Dokumentation, Testabdeckung und statischer Analyse (Linting, Security Findings). Für die Enterprise-Readyness sind RBAC, i18n, White Labeling, eine Benutzerdokumentation sowie Massnahmen im Bereich Styling, Accessibility und UX notwendig.

**Aufwand:** Der geschätzte Aufwand liegt bei 114 Personentagen.
