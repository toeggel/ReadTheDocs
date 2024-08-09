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

# Testing

- EfCore.SchemaCompare (https://github.com/JonPSmith/EfCore.SchemaCompare) allows easy schema comparison against the C# models (entities).
```csharp
[Test]
public void DatabaseDeployed_SchemaCompared_TableAndPropertyAndNullabilityMatchesEntityAndColumn()
{
	var comparer = new CompareEfSql();
	comparer.CompareEfWithDb(_context);

	var logs = comparer.Logs;
	var tableMismatches = logs.Single().SubLogs.Where(l => l.State == CompareState.NotInDatabase && l.Type == CompareType.Entity).ToList();
	var propertyMismatches = logs.Single().SubLogs.SelectMany(l => l.SubLogs).Where(l => l.State == CompareState.NotInDatabase && l.Type == CompareType.Property).ToList();
	var nullabilityErrors = logs.Single().SubLogs.SelectMany(l => l.SubLogs).Where(l => l.State == CompareState.Different && l.Type == CompareType.Property && l.Attribute == CompareAttributes.Nullability).ToList();

	tableMismatches.ShouldBeEmpty();
	propertyMismatches.ShouldBeEmpty();
	nullabilityErrors.ShouldBeEmpty();
}
```
- We can also compare the tables against our Entities
```csharp
    [Test]
public async Task DatabaseDeployed_SchemaCompared_EntityMatchesTable()
{
	var tables = await _sysContext.Tables.Include(t => t.Columns).AsNoTracking().ToListAsync();
	var entities = Assembly.GetAssembly(typeof(MyEntity))!.GetTypes().Where(t => t.IsClass && t.GetInterfaces().Contains(typeof(IBaseEntity)));
	foreach (var table in tables)
	{
		var entity = entities.SingleOrDefault(e => e.GetCustomAttributes<TableAttribute>().Any() && e.GetCustomAttribute<TableAttribute>()!.Name == table.Name);
		if (entity != null)
		{
			foreach (var column in table.Columns)
			{
				entity.GetProperties().Any(p => p.Name == column.Name).ShouldBeTrue($"Column {column.Table.Name}.{column.Name} is missing in entity {entity.Name}.");
			}
		}
	}
}
```
