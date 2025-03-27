---
aliases: 
tags:
  - classes
  - objects
  - csharp
  - grundlagen
  - oop
---

## Was ist eine Klasse

Eine **Klasse** ist eine Vorlage oder ein Bauplan für Objekte. Sie beschreibt, wie Objekte aufgebaut sind (Attribute) und wie sie sich verhalten (Methoden). Klassen bilden den Kern der objektorientierten Programmierung (OOP).

**Definition einer Klasse:**

```csharp
public class Car
{
	// Eigenschaften (Attribute)
	public string Brand;
	public string Model;
	public int Speed;

	// Konstruktor
	public Car(string _brand, string _model)
	{
		Brand = _brand;
		Model = _model;
		Speed = 0; // Standardwert
	}


	// Methoden
	public void Acceleration(int _value)
	{
		Speed += _value;
	}

	public void Brake(int _value)
	{
		Speed -= _value;
	}

	public void Display()
	{
		Console.WriteLine($"Auto: {Brand} {Model}, Geschwindigkeit: {Speed} km/h");
	}
}
```



## Was ist ein Objekt

Ein **Objekt** ist eine Instanz (konkrete Ausprägung) einer Klasse. Jede Instanz hat eigene Werte für ihre Eigenschaften und kann Methoden der Klasse nutzen.

**Erstellen eines Objekts (Instanziieren):**

```csharp
Car myCar = new Car("BMW", "X5");
```

**Zugriff auf Eigenschaften und Methoden:**

```csharp
myCar.Acceleration(50);
myCar.Brake(20);
myCar.Display(); // Ausgabe: Auto: BMW X5, Geschwindigkeit: 30 km/h
```



## Klassen vs. Objekte (Zusammenfassung)


| Klasse                                | Objekt                                      |
| ------------------------------------- | ------------------------------------------- |
| Bauplan / Vorlage                     | Konkrete Umsetzung einer Klasse             |
| Allgemeine Beschreibung               | Individuelle Instanz der Klasse             |
| Definiert Eigenschaften und Verhalten | Besitzt spezifische Werte für Eigenschaften |


### Wichtige Begriffe rund um Klassen


| Begriff                       | Erklärung                                                                                             |
| ----------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Attribute (Eigenschaften)** | Variablen, die Daten eines Objekts speichern.                                                         |
| **Methoden (Verhalten)**      | Funktionen, die Operationen oder Aktionen durchführen.                                                |
| **Konstruktor**               | Spezielle Methode zum Initialisieren eines Objekts. Wird bei Objekterstellung automatisch aufgerufen. |
| **Instanziierung**            | Prozess der Erstellung eines Objekts aus einer Klasse.                                                |
| **Instanz**                   | Konkretes Objekt, erstellt aus einer Klasse.                                                          |


### Zugriffsmodifizierer in Klassen (Attribute und Methoden)

Steuern die **Sichtbarkeit** einzelner Bestandteile einer Klasse.

| Zugriffsmodifizierer | Beschreibung                                              |
| -------------------- | --------------------------------------------------------- |
| **public**           | Zugriff von überall möglich                               |
| **private**          | Zugriff nur innerhalb der eigenen Klasse                  |
| **protected**        | Zugriff nur innerhalb der Klasse und abgeleiteten Klassen |
| **internal**         | Zugriff nur innerhalb der gleichen Assembly (Projekt)     |



## Besondere Arten von Klassen

### Abstrakte Klassen

Können nicht direkt instanziiert werden, dienen als Vorlage für Unterklassen.

```csharp
public abstract class Animal
{
	public string Name;
	public abstact void PlaySound();
}

public class Dog : Animal // Vererbung
{
	public override void PlaySound()
	{
		Console.WriteLine("Wuff!");
	}
} 
```


### Statische Klassen

Können nicht instanziiert werden und beinhalten nur statische Mitglieder.

```csharp
public static class Math
{
	public static int Add(int a, int b) => a + b;
}

// Aufruf ohne Instanziierung
int sum = Math.Add(3, 6); // 9
```



#### Wichtige Fakten und Tipps:

- Klassen sollten klar definierte Aufgaben und Zuständigkeiten haben (**Single Responsibility Principle**).
- Attribute sollten idealerweise **private** sein; Zugriff über **öffentliche Methoden** oder **Properties**.
- Konstruktoren sind wichtig für eine **korrekte Initialisierung der Objekte**.