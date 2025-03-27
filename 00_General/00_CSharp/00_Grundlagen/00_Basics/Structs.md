---
aliases: 
tags:
  - struct
  - csharp
  - grundlagen
  - oop
---

## Structs in C#

### Was ist ein Struct

Ein **Struct** (kurz für "Structure") ist in C# eine Datenstruktur, die ähnlich wie eine Klasse aufgebaut ist, aber einige wesentliche Unterschiede aufweist:

- Ein Struct ist ein **Werttyp** (**Value Type**).
- Ein Struct speichert Daten direkt auf dem Stack (außer wenn er Teil eines Objekts auf dem Heap ist).
- Structs eigenen sich besonders gut für kleine Datenmengen, die häufig erstellt und zerstört werden.



| Eigenschaften       | Struct                                                                | Klasse                                  |
| ------------------- | --------------------------------------------------------------------- | --------------------------------------- |
| **Typ**             | Werttyp (Value Type)                                                  | Referenztyp (Reference Type)            |
| **Speicherort**     | Stack (meistens)                                                      | Heap                                    |
| **Vererbung**       | Nicht möglich, aber Interfaces erlaubt                                | Vererbung erlaubt                       |
| **Standartwert**    | Immer definiert (kann nicht **null** sein, außer als nullable struct) | Kann **null** sein                      |
| **Kopierverhalten** | Beim Zuweisen entsteht eine Kopie                                     | Beim Zuweisen wird Referenz kopiert     |
| **Performance**     | Sehr gut für kleine Datenmengen                                       | Besser geeignet für größere Datenmengen |

### Definition eines Structs

Ein Struct wird mit dem Schlüsselwort **struct** definiert:

```csharp
public struct Point
{
	public int X;
	public int Y;

	// Konstruktor (muss alle Felder initialisieren)
	public Point(int _x, int _y)
	{
		X = _x;
		Y = _y;
	}

	// Methode in Struct
	public void Display()
	{
		Console.WriteLine($"Punkt: ({X}, {Y})");
	}
}
```


**Verwendung**:

```csharp
Point p1 = new Point(10, 20);
p1.Display(); // Ausgabe: Punkt: (10, 20)

// Kopie durch Zuweisung
Point p2 = p1;
p2.X = 50;

p1.Display(); // Ausgabe: Punkt: (10, 20)
p2.Display(); // Ausgabe: Punkt: (50, 20)
```

>[!warning]- Beim Zuweisen entsteht eine **Kopie**, da Structs **Werttypen** sind.


### Wann sollte ein Struct verwendet werden

Verwende ein Struct, wenn:

- Du kleine Datenmengen bündelst (z. B. Punkt-Koordinaten, RGB-Werte).
- Du viele temporäre Instanzen benötigst (Performance-Vorteil durch Stack).
- Du klare Wert-Semantik möchtest (Zuweisungen erzeugen Kopien).

**Beispiele** sinnvoller Structs:

- Punkt (Koordinaten)
- Farbe (RGB-Farben)
- Vektor (Mathematik)
- Datum oder Zeitintervalle


### Wann sollte besser eine Klasse verwendet werden

Verwende Klassen, wenn:

-  Du komplexe Objekte mit vielen Funktionalitäten erstellst.
- Du Vererbung benötigst.
- Dein Objekt verändert werden soll, ohne Kopien anzulegen (**Referenzsemantik**)



## Good To Know

### Structs und Standartwerte

Structs haben immer einen Standartwert:

```csharp
Point p = new Point(); // X und Y sind automatisch 0
p.Display(); // Ausgabe: Punkt: (0, 0)
```

>[!info]- Bei Klassen wäre der Standardwert **null**


### Einschränkungen von Structs

- Ein Struct kann **nicht** von einer anderen Klasse oder einem Struct erben.
- Ein Struct kann **nicht** als Basisklasse dienen (ist immer "sealed").
- **Parameterlose Konstruktoren** sind seit C# 10 möglich, davor mussten Konstruktoren immer alle Felder initialisieren
- Ein Struct kann Interfaces **implementieren**


```csharp
interface IDisplay
{
	public void Display();
}

struct Point : IDisplay
{
	public int X;
	public int Y;

	public Point(int _X, int _Y)
	{
		X = _x;
		Y = _y;
	} 

	public void Display()
	{
		Console.WriteLine($"Punkt: ({X}, {Y})");
	}
}
```



### Nullable Structs

Structs können als Nullable definiert werden (**?**):

```csharp
Point? nullablePoint = null;

if(nullablePoint.HasValue)
{
	nullablePoint.Value.Display();
}
else
{
	Console.WriteLine("Kein Wert vorhanden.");
}
```



#### Beispiel Struct vs. Klasse

Verdeutlichung der unterschiedlichen Verhaltensweisen:

**Struct (Werttyp)**:

```csharp
struct MyStruct
{
	public int Value;
}

MyStruct a = new MyStruct { Value = 5};
MyStrcut b = a; // Kopie erzeugt
b.Value = 10;

Console.WriteLine(a.Value); // 5 unverändert
Console.WriteLine(b.Value); // 10
```


**Klasse (Referenztyp)**:

```csharp
class MyClass
{
	public int Value;
}

MyClass a = new MyClass { Value = 5};
MyClass b = a; // Referenz kopiert
b.Value = 10;

Console.WriteLine(a.Value); // 10 (durch Referenz geändert)
Console.WriteLine(b.Value); // 10
```


>[!warning]- Performance-Überlegung
> - **Structs** haben oft Vorteile bei kleinen Datensätzen (wenige Bytes).
> - Für größere Datensätze (mehrere Felder oder Referenzen) sind Klassen oft besser (weniger Speicherverbrauch durch Heap-Verwaltung).


>[!warning]- Wichtigste Regeln und Hinweise
> - Structs sollten **klein und unveränderlich** sind (immutable).
> - Vermeide komplexe Structs (Speicher-Performance kann sinken).
> - Achte auf das Kopieverhalten, das sich von Klassen unterscheidet.

