---
tags:
  - Database
---

# Datenarchitektur

Folgende Punkte sind entscheidende Themen bzw. Fragen zur Datenarchitektur:

* SQL oder NoSQL?
* Datenzugriff (API, ORM)
* Authentisierung und Autorisierung des Datenbankzugriffs (simpel oder komplex)
* Datenbank-Updates (transitions- oder zustandsbasiert und Wahl des Werkzeugs)
* Datenbanktests und Testdaten (Anonymisierung)
* Datenmigration und -abgleich (Big Bang oder Koexistenz)
* Datenexport für Datahub
* Cross-Boundary Data Access Pattern (Web Gateway, Data Aggregator, Service-to-Service, Materialized View)
* Event Driven Architecture (Event Sourcing, CQRS, Event Notification, Event-Carried State Transfer)
* Datenschutz, Kryptographie und Compliance (GDPR)
* Data Dictionary: Auswahl des Werkzeugs (Microsoft Azure Data Catalog?)
* Änderungsverfolgung (Audit Trail, temporale Datenbank, Document-Versioning-Pattern)
* Verfügbarkeit
* Master Data Management
* Datenqualität
* Datenbank-Backup und -Retention
* Datenredundanz (Datenreplikation, Materialized Views)
* Bulk Data Exchange
* Datenkonsistenz (verteilte Transaktionen, SAGA)

# Optimization

- Using AND queries can use indexes where OR queries cannot. Therefore we can optimize queries like that (only do it if there is actually a performance issue)

```csharp
// this is performanter
var persons = await _context.Person
.Where(p => p.Function == Function.Important && p.Status == Status.Active)
.Union(_context.Person.Where(p => p.IsInternalUser && p.Status == Status.Active))
.ToListAsync();

// instead of
var persons = await _context.Person
.Where(p => p.Status == Status.Active && (p.Function == Function.Important || p.IsInternalUser))
.ToListAsync();

```

# Concurrency 

**Optimistic Concurrency** is more suitable when conflicts are less likely, while **Pessimistic Concurrency** is used when conflicts are anticipated

**Optimistic Concurrency** => use RowVersion column in DB and property in model
**Pessimistic Concurrency** => use Transactions
