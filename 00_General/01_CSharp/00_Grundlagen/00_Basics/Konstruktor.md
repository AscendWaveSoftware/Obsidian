---
aliases: 
tags:
  - csharp
  - konstruktor
  - grundlagen
  - oop
  - klassen
  - fabricmethod
---

Klassen haben spezielle Methoden, die nur dazu dienen, die Klasse zu erzeugen. Diese Methoden heißen **Konstruktoren**. Eine Klasse kann mehrere Konstruktoren haben, sie hat aber mindestens einen Konstruktor. Jede Klasse besitzt einen sogenannten **Standard-Konstruktor**. Diesen Konstruktor hat eine Klasse automatisch, wenn kein Konstruktor deklariert wird. 

```csharp
class KonsolenApp
{
	string begruessung = "Hallo Welt!";

	// Konstruktor ohne Argumente
	public KonsolenApp()
	{
		
	}

	public void Start()
	{
		Console.WriteLine(begruessung);
	}
}
```


Der **Konstruktor** wird deklariert wird eine Methode, die den gleichen Namen hat wie die Klasse. Allerdings wird für einen Konstruktor kein Rückgabetyp angegeben. Der **Rückgabewert** eines Konstruktors ist seine Klasse.

```csharp
class KonsolenApp
{
	string begruessung = "Hallo Welt";

	// Konstruktor mit Übergabeparameter
	public KonsolenApp(string _begruessung)
	{
		begruessung = _begruessung;
	}

	public void Start()
	{
		Console.WriteLine(begruessung);
	}
}
```


### Überladen eines Konstruktors

Genauso wie Methoden können auch Konstruktoren überladen werden:

```csharp
class KonsolenApp
{
	string begruessung = "Hallo Welt!";

	// Konstruktor ohne Übergabeparameter
	public KonsolenApp()
	{
	
	}

	// Konstruktor mit Übergabeparameter
	public KonsolenApp(string _begruessung)
	{
		begruessung = _begruessung;
	}

	public void Start()
	{
		Console.WriteLine(begruessung);
	}
}
```


### Fabric Method

Eine **Fabrik-Methode** ist eine statische Methode, die ein Objekt der Klasse erzeugt. Die Methode muss statisch sein, damit direkt über die Klassen aufgerufen werden kann, ohne vorher ein Objekt zu erzeugen. Das Erzeugen des Objekts soll die Fabrik-Methode übernehmen.

```csharp
public static KonsolenApp InSpanish()
{
	var instance = new KonsolenApp("Hola Mundo!");
	return instance;	
}
```

Der **Rückgabewert** der Fabrik-Methode ist hier **KonsolenApp**. Wir wollen das Objekt schließlich erzeugen. In der Fabrik-Methode erzeugen wir das Objekt mit einem Konstruktor, der den Wert "Hola Mundo!" entgegennimmt und dann geben wir das Objekt zurück. Damit haben wir eine Fabrik-Methode, die ein KonsolenApp-Objekt erzeugt, das mit einer spanischen Begrüßung initialisiert ist. Bei der Verwendung des Objekts müssen keine Daten zur Initialisierung zugewiesen werden.  

