---
aliases: 
tags:
  - lambdaausdruck
  - csharp
  - fortgeschritten
  - syntacticsugar
---

## Was ist ein Lambda-Ausdruck

Ein **Lambda-Ausdruck** ist eine anonyme Funktion, die inline an Stellen verwendet werden kann, an denen [[Delegates]] oder [[Expression Trees]] erwartet werden. Er kombiniert **Parameterliste** und einen **Ausdruck oder Block** zu einer kompakten Schreibweise.


### Grundsyntax

- **Expression Lambda** (einzeilige Ausdrucksform):

```csharp
(Parameterliste) => Ausdruck
```

#### Beispiel:

```csharp
x => x * x // Quadrieren: Eingabe x, gibt x*x zurück
(a, b) => a + b // Addition zweier Werte
() => DateTime.Now // Keine Parameter, gibt aktuelles Datum/Zeit
```


- **Statement Lambda** (Blockform mit mehreren Anweisungen):

```csharp
(Parameterliste) =>
{
	// mehrere Statements
	Console.WriteLine(parameter);
	return Ergebnis;
}
```

#### Beispiel:

```csharp
(int x, int y) =>
{
	Console.WriteLine($"Addiere {x} und {y}");
	return x + y;
}
```


### Verwendung mit [[Delegates]] und [[Func/Action]]

#### 1. Action<...>
Delegaten ohne Rückgabewert:

```csharp
Action<string> drucker = s => Console.WriteLine(s);
drucker("Hallo Lambda!");
```

#### 2. Func<...>
Delegaten mit Rückgabewert; letzter Typ ist Rückgabetyp:

```csharp
Func<int, int, int> add = (a, b) => a + b;
int summe = add(3, 5); // 8
```

#### 3. Predicate<>
Spezieller Delegate, der bool zurückgibt:

```csharp
Predicate<int> istGerade = x => x % 2 == 0;
bool test = istGerade(4); // true
```


### Typinferenz vs. explizite Typangabe

- **Typinferenz** (meist bevorzugt)

```csharp
Func<int, int> verdoppeln = x => x * 2;
```


- **Explizite Typangabe** (wenn nötig, z. B. bei Mehrdeutigkeit):

```csharp
Func<int, int> verdoppeln = (int x) => x * 2;
Func<int, int, int> pow = (int a, int b) => (int)Math.Pow(a, b);
```



## Einsatz in LINQ

Lambda-Ausdrücke sind das Herzstück der Mehtod-Syntax von LINQ:

```csharp
int[] zahlen = { 1, 2, 3, 4, 5, 6 };

var gerade = zahlen
	.Where(x => x % 2 == 0) // Filter
	.Select(x => x * x) // Projektion
	.OrderByDescending(x => x) // Sortierung
```


## Closures: Variablenbindung

Lambda-Ausdrücke "schließen" externe Variablen ein (**Closure**), d. h. sie können lokale Variablen referenzieren:

```csharp
int faktor = 3;
Func<int, int> mult = x => x * faktor;

Console.WriteLine(mult(5)); // 15

faktor = 10;
Console.WriteLine(mult(5)); // 50 (Closure nutzt aktuellen Wert)
```



>[!warning]- **Hinweis**: Vorsicht bei Schleifen:

```csharp
var actions = new List<Action>();
for (int i = 0; i < 3; i++)
{
	actions.Add(() => Console.WriteLine(i));
}
actions.ForEach(a => a());
// Ausgabe: 3, 3, 3
// Besser: Kopie der Variable
for (int i = 0; i < 3; i++)
{
	int copy = i;
	actions.Add(() => Console.WriteLine(copy));
}
```


## Statement vs. Expression Lambdas

| Merkmal              | Expression Lambda           | Statement Lambda          |
| -------------------- | --------------------------- | ------------------------- |
| **Syntax**           | `(args) => Ausdruck`        | `(args) => { Anweisung }` |
| **Rückgabewert**     | implizit (aus dem Ausdruck) | explizit mit `return`     |
| **Mehrere Statements | ❌                           | ✅                         |

## Best Practices

- **Kürze bewahren**: Nutze **Expression Lambdas** für simple Operationen.
- **Lesbarkeit**: Bei komplexer Logik besser **Statement Lambdas** oder benannte Methoden verwenden.
- **Typinferenzen**: Vertraue auf den Compiler, außer es entsteht Mehrdeutigkeit.
- **Vermeide Capture-Fallen**: Achte auf Closure-Verhalten in Schleifen und Asynchronität.
- **Delegate-Typwahl**: Verwende `Func<>, Action<>` oder eigene Delegates passend zum Szenario. 


## Fazit
- **Lambda-Ausdrücke** sind kompakte, anonyme Funktionen.
- Sie ermöglichen sauberen, deklarativen Code - besonders in Kombination mit LINQ.
- **Closures** schaffen mächtige Patterns, erfordern jedoch Aufmerksamkeit.
- **Expression Lambdas** für einfache Ausdrücke; **Statement Lambdas** für komplexere Logik.