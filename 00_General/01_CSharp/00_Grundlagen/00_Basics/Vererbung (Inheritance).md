---
aliases:
  - inheritance
tags:
  - vererbung
  - abstraction
  - inheritance
  - csharp
  - grundlagen
  - oop
  - klassen
---

## Was ist Vererbung

**Vererbung** ermöglicht es, von einer bestehenden Klasse (**Basisklasse**) zu erben und eine neue Klasse (**abgeleitete Klasse**) zu erstellen, die alle Eigenschaften und Methoden der Basisklasse nutzt und bei Bedarf erweitert oder anpasst.

#### Grundsyntax

```csharp
// Basisklasse (Parent)
public class Tier
{
	public string Name { get; set; }
	
	public void Essen()
	{
		Console.WriteLine($"{Name} isst.");
	} 
}

// Abgeleitete Klasse (Child)
public class Hund : Tier
{
	public void Bellen()
	{
		Conosole.WriteLine($"{Name} bellt.");
	}
}
```

- **Hund** erbt automatisch **Name** und **Essen()** von **Tier**.
- Zugriff auf Basismitglieder wie auf eigene Mitglieder.


### Konstruktoren in Vererbung

- **Basisklassen-Konstruktor** wird vor dem abgeleiteten ausgeführt.
- Mit **base(...)** kann man gezielt den Konstruktor der Basisklasse aufrufen.

```csharp
public class Tier
{
	public string Name { get; set; }

	public Tier(string _name)
	{
		Name = _name;
	}
}

public class Hund : Tier
{
	public string Rasse { get; }

											// Aufruf des Tier-Konstruktors
	public Hund(string _name, string _rasse):base(_name) 
	{
		Rasse = _rasse;
	}
}
```


### Überschreiben von Methoden (virtual / override)

- Eine Mehtode in der Basisklasse muss als **virtual (oder abstract)** markiert sein, um sie überschreiben zu können.
- In der abgeleiteten Klasse verwendet man **override**.

```csharp
public class Tier
{
	public virtual void LautGeben()
	{
		Console.WriteLine("Tier macht ein Geräusch.");
	}
}

public class Hund : Tier
{
	public override void LautGeben()
	{
		Console.WriteLine("Wuff!");
	}
}
```

- Aufruf über Basistyp entscheidet zur Laufzeit, welche Implementierung verwendet wird (**Polymorphie**).


### Vererbung von Methoden (new)

- Mit **new** kann man eine Methode der Basisklasse **verbergen**, statt sie zu überschreiben.
- Vorsicht: Kehrt nicht das Laufzeit-Polymorphie-Verhalten um.

```csharp
public class Tier
{
	public void LautGeben()
	{
		Console.WriteLine("Tier macht Geräusche.");
	}
}

public class Katze : Tier
{
	public new void LautGeben()
	{
		Console.WriteLine("Miau!");
	}
}
```

- Wird über ==Tier t = new Katze(); t.LautGeben();== aufgerufen, kommt die Basisklasse-Version zum Einsatz.


## Abstrakte Klassen und Methoden

- **Abstrakte Klasse** kann nicht instanziiert werden.
- **Abstrakte Methode** definiert nur Signatur; muss in abgeleiteten Klassen implementiert werden.

```csharp
public abstract class Tier
{
	public string Name { get; set; }
	public abstract void LautGeben();
}

public class Vogel : Tier
{
	public override void LautGeben()
	{
		Console.WriteLine("Zwitscher!");
	}
}
```


## Sealed-Klassen und Mehtoden

- **sealed class**: Kann nicht weiter vererbt werden.
- **sealed override**: Verhindert, dass abgeleitete Klassen diese Methode erneut überschreiben.

```csharp
public class Tier
{
	public virtual void Essen(){ }
}

public class Hund : Tier
{
	public sealed override void Essen()
	{
		Console.WriteLine();
	}
}

// public class Welpe : Hund {} // Fehler: Hund ist nicht sealed
```


## Zugriffsmodifizierer in Vererbung


| Modifizierer           | Sichtbarkeit für abgeleitete Klassen |
| ---------------------- | ------------------------------------ |
| **public**             | Ja                                   |
| **protected**          | Ja (auch außerhalb der Assembly)     |
| **internal**           | Ja, wenn in derselben Assembly       |
| **protected internal** | Ja, in Assembly oder abgeleitet      |
| **private**            | Nein                                 |

- **protected** erlaubt Ableitenden Zugriff, aber nicht "außenstehenden" Code.

```csharp
public class Basis
{
	protected int geschuetztesFeld;
}

public class Ableitung : Basis
{
	public void Test()
	{
		geschuetztesFeld = 5; // erlaubt
	}
}
```


## Mehrfachvererbung

- **Nicht unterstützt** für Klassen
- Stattdessen: **Interfaces** zur Mehrfachverwendung von Signaturen.

```csharp
public interface IFliegbar { void Fliegen(); }
public interface ISchwimmbar { void Schwimmen; }

public class Ente : IFliegbar, ISchwimmbar
{
	public void Fliegen() { /*  */ }
	public void Schwimmen() { /*  */ }
}
```


## Zusammenfassung der Key-Keywords


| Keyword         | Bedeutung                                          |
| --------------- | -------------------------------------------------- |
| **class A : B** | A erbt von B                                       |
| **virtual**     | Methode kann überschrieben werden                  |
| **override**    | Überschreibt eine virtuelle/abstrakte Methode      |
| **new**         | Verbirgt ein Basismitglied                         |
| **abstract**    | Klasse/Methode ohne Implementierung                |
| **sealed**      | Verhindert weitere Vererbung oder Überschreibung   |
| **base**        | Referenz auf die Basisklasse (Konstruktor/Methode) |
| **protected**   | Sichtbar in Klasse und allen Abgeleiteten          |



