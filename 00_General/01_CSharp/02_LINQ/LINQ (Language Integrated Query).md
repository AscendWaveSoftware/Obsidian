---
aliases: 
tags:
  - linq
  - datenbanken
  - query
  - csharp
---

## Was ist LINQ

**LINQ (Language Integrated Query)** ist ein in C# integriertes Abfragesystem, mit dem Datenquellen (wie Arrays, Listen, XML, Datenbanken) deklarativ abgefragt und transformiert werden können. Es bringt SQL-ähnliche Syntax in die .NET-Programme und nutzt **Extension Methods** und **Lambda-Ausdrücke**, um lesbaren, kompakten Code zu schreiben.


## LINQ-Varianten (Provider)


| Provider               | Datenquelle                                  |
| ---------------------- | -------------------------------------------- |
| **LINQ to Objects**    | In-Memory-Collections (z. B. List<T>, Array) |
| **LINQ to SQL**        | Relationale Datenbanken via ADO.NET          |
| **LINQ to Entities**   | Entity Framework                             |
| **LINQ to XML**        | XML-Dokumente                                |
| **PLINQ**              | Parallele Ausführung von LINQ-Abfragen       |
| **LINQ to SharePoint** | Zugriff auf SharePoints-Daten                |


## Syntaxformen

#### 1. Query Syntax (SQL-ähnlich)

```csharp
int[] zahlen = { 1, 2, 3, 4, 5, 6 };

var gerade =
	from z in zahlen
	where z % 2 == 0
	orderby z descending
	select z;

foreach(var z in gerade)
	Console.WriteLine(z); // 6, 4, 2
```

#### 2. Method Syntax (Fluent API)

```csharp
var gerade = zahlen
	.Where(z => z % 2 == 0)
	.OrderByDescending(z => z)
	.Select(z => z);

gerade.ToList().ForEach(Console.WriteLine);
```

>[!warning]- Unter der Haube basiert die Query-Syntax auf Mehtod Calls - beides ist identisch performant.



## Wichtige LINQ-Operatoren


| Kategorie           | Methode(n)                                                              | Beschreibung                                |
| ------------------- | ----------------------------------------------------------------------- | ------------------------------------------- |
| **Filter**          | **Where(predicate)**                                                    | Elemente auswählen                          |
| **Projektion**      | **Select(selector), SelectMany(selector)**                              | Transformation von Objekten                 |
| **Sortierung**      | **OrderBy(key), OrderByDescending(key), ThenBy(...)**                   | Auf- oder Absteigend sortieren              |
| **Gruppierung**     | **GroupBy(keySelector)**                                                | Elemente in Gruppen einteilen               |
| **Aggregation**     | **Count(), Sum(), Min(), Max(), Average(), Aggregate()**                | Auswertung über die Gesamtheit              |
| **Menge**           | **Distinct(), Union(), Intersect(), Except()**                          | Mengenoperatoren                            |
| **Element**         | **First(), FirstOrDefault(), Single(), SingleOrDefault(), ElementAt()** | Einzelne Elemente abfragen                  |
| **Verkettung**      | **Concat(), Zip()**                                                     | Zwei Sequenzen kombinieren                  |
| **Join**            | **Join(), GroupJoin()**                                                 | Verknüpfen von Sequenzen (inner/outer Join) |
| **Partitionierung** | **Take(n), Skip(n), TakeWhile(cond), SkipWhile(cond)**                  | Teilmengen extrahieren                      |


## Deferred vs. Immediate Execution

- **Deferred Execution:** Abfrage wird erst beim Iterieren (foreach, ToList(), Count(), ...) ausgeführt.

```csharp
var query = zahlen.Where(z => 3);
// keine Ausführung bis hier
int anzahl = query.Count(); // jetzt Ausführung
```

- **Immediate Execution:** Rückgabe eines konkreten Ergebnisses, sofortige Ausführung.
-  **Methoden:** **ToList(), ToArray(), Count(), Sum()** etc.


### Beispiel Kombination mehrerer Operatoren

```csharp
List<Person> personen = new () {
	new("Anna", 28, "W"),
	new("Ben", 35, "M"),
	new("Clara", 22, "W"),
	new("David", 28, "M"),
};

// 1) Filter: Alter > 25
// 2) Sortierung: nach Name
// 3) Projektion: nur Name-String
var ergebnis = personen
	.Where(p => p.Alter > 25)
	.OrderBy(p => p.Name)
	.Select(p => p.Name);

foreach(var name in ergebnis)
	Console.WriteLine(name); // Anna, Ben, David
```


### GroupBy & Aggregation

```csharp
var gruppen = personen
	.GroupBy(p => p.Alter)
	.Select(g => new {
		Alter = g.Key,
		Anzahl = g.Count(),
		Namen = g.Select(p => p.Name).ToList()
	});

foreach(var g in gruppen)
	Console.WriteLine($"Alter {g.Alter}: {g.Anzahl} Person(en) - {string.Join(", ", g.Name)}");
```



### Join von zwei Sequenzen

```csharp
var orders = new[] {
	new { OrderId = 1, CustomerId = 1 },
	new { OrderId = 2, CustomerId = 2 },
};

var customers = new[] {
	new { CustomerId = 1, Name = "Anna" },
	new { CustomerId = 2, Name = "Ben" },
};

var join = orders.Join(
	customers,
	o => o.CustomerId,
	c => c.CustomerId,
	(o, c) => new { o.OrderId, c.Name }
);

foreach(var x in join)
	Console.WriteLine($"Order {x.OrderId} von {x.Name}");
```



## Tipps & Best Practices

- **Benutze Method Syntax** für komplexere Abfragen, da sie besser in IDEs auto-vervollständigt wird.
- **Cache Ergebnisse (ToList())**, wenn du mehrmals iterierst und die Datenquelle teuer ist.
- **Vermeide unnötige Neuberechnungen:** Kette Operatoren in einer Abfrage
- **Verwende AsEnumerable() oder AsQueryable()** bewusst, um zwischen LINQ to Objects und LINQ to Entities zu wechseln.
- **Nutze SelectMany** für flache Listen aus geschachtelten Strukturen (z. B. IEnumerable<IEnumerable<>>).



## Fazit 

**LINQ** vereinfacht **Datentransformationen und -abfragen** in C# deutlich, erhöht die Lesbarkeit und reduziert **Boilerplate-Code**. Mit den hier vorgestellten Operatoren und Patterns kann nahezu jede Datenmanipulation elegant realisieret werden - von einfachen Filtern bis zu komplexen Joins und Gruppierungen. 