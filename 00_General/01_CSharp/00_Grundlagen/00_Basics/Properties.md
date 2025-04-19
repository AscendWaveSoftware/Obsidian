---
aliases:
  - eigenschaften
tags:
  - properties
  - variablen
  - csharp
  - grundlagen
---

## Was sind Properties

**Properties** sind spezielle Member in Klassen und Structs, die den Zugriff auf Felder kapseln und gleichzeitig wie öffentliche Variablen verwendet werden können. Sie ermöglichen Kontrolle über das **Lesen** und **Schreiben** von Daten.

### Grundstruktur einer Property

```csharp
private int alter;

public int Alter
{
	get { return alter; }
	set { alter = value; }
}
```

- **get**: Zugriff (Lesen) auf den Wert.
- **set**: Zuweisung (Schreiben) des Wertes.


### Auto-implemented Properites

Wenn kein zusätzliches Feld benötigt wird, kann C# automatisch ein **Backing Field** generieren:

```csharp
public string Name { get; set; } // Standard read/write
public int Age { get; private set; } // Öffetnlich lesbar, intern/ set privat
```

- Compiler legt unsichtbares Feld an.
- Kürzerer und übersichtlicher Code.


### Read-only / Write-only / Init-only


| Typ                  | Erklärung                                            | Beispiel                                       |
| -------------------- | ---------------------------------------------------- | ---------------------------------------------- |
| **Read-only**        | nur **get**, kein **set**                            | public int ID { get; }                         |
| **Write-only**       | nur **set**, kein **get** (selten genutzt)           | public string Passwort { set {_pw = value; } } |
| **Init-only (C#9+)** | **set** nur während Objektinitialisierung (**init**) | public string Titel { get; init; }             |

```csharp
public class Buch
{
	public int ID { get; } // Read-only
	public string Titel { get; init; } // Init-only
	public decimal Preis { get; private set; } // Privat setzbar

	public Buch(int _id, string _titel, decimal _preis)
	{
		ID = _id;
		Titel = _titel;
		Preis = _preis;
	}
}
```


### Expression-bodied Properties (C#6+)

Kurzschreibweise für einfache Getter/Setter oder Berechnungen:

```csharp
public int Breite { get; set; }
public int Hoehe { get; set; }

// Ausdruckseigenschaft
public int Flaeche => Breite * Hoehe;
```

- **=>** für prägnante, einzeilige Properties.


### Property mit Validierung

Man kann im **set** zusätzliche Logik einbauen:

```csharp
private int alter;

public int Alter
{
	get => alter;
	set 
	{
		if(value < 0) throw new ArgumentOutOfRangeException(nameof(value), "Alter muss mindestens >= 0 sein");
		alter = value;
	}
}
```

- Gut für Validierungen, Logging, Benachrichtigungen (z. B. INotifiyPropertyChanged)


#### Zugriffsmodifizierer für get/set

```csharp
public string Name { get; private set; } // Nut intern/set
internal int Score { get; protected set; } // Nur Assembly/get, abgeleitet/set
```

- Gibt feinkörnige Kontrolle über Zugriff


### Statische Properties

**Static Properties** gehören zu Klassen, nicht zur Instanz:

```csharp
public class Konfiguration
{
	public static string AppName { get; set; } = "MeineApp";
}
```

- Zugriff: **Konfiguration.AppName**.


### Properties in Interfaces

Interfaces dürfen Properties deklarieren, die dann implementiert werden: 

```csharp
public interface IPerson
{
	string Name { get; set; }
	int Alter { get; }

	public class Mitarbeiter : Person
	{
		public string Name { get; set; }
		public int Alter { get; private set; }
	
		public Mitarbeiter(string _name, int _alter)
		{
			Name = _name;
			Alter = _alter;
		} 
	}
}
```



## Zusammenfassung der Key Patterns


| Pattern                      | Syntax                               | Zweck                                |
| ---------------------------- | ------------------------------------ | ------------------------------------ |
| **Auto-Property**            | public T Prop { get; set; }          | Schnellstes Grundgerüst              |
| **Read-only**                | public T Prop { get; }               | Nur öffentlich lesen                 |
| **Init-only**                | public T Prop { get; init; }         | Setzen nur bei Objektinitialisierung |
| **Expression-bodied Getter** | public T Prop => Ausdruck;           | Einzeilige Berechnungen              |
| **Private Setter**           | public T Prop {  get; private set; } | Intern verändern, extern lesen       |
| **Validierung im Setter**    | set { if()... }                      | Datenintegrität sicherstellen        |


## Fazit

- **Properties** sind die empfohlene Art, Felder in C# zu kapseln.
- Sie bieten **Kapselung**, **Validierung** und **flexible Zugriffsteuerung**.
- **Auto-implemented** und **init-only** erleichtern kurze, deklarative Definitionen.

