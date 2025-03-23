---
aliases: 
tags:
  - switch
  - csharp
  - grundlagen
  - booleans
  - schleifen
---
## C# Switch Statements

Das **switch-Statement** wird verwendet, um einen von mehreren Codeblöcken auszuwählen, der ausgeführt werden soll:

```csharp
switch (expression)
{
	case x:
	// code block
		break;
	case y:
	// code block
		break;
	default
	// code block
		break;
}
```

### So funktioniert das switch-Statement:

1. Der **Switch-Ausdruck** wird einmal ausgewertet.
2. Der Wert des Ausdrucks wird mit den Werten der einzelnen **Fälle** verglichen.
3. Wenn es eine Übereinstimmung gibt, wird der zugehörige Codeblock ausgeführt.


Folgendes Beispiel verwendet die Wochentagenummer zur Berechnung des Wochentagnamens:

```csharp
int day = 4;

switch(day)
{
	case 1:
		Console.WriteLine("Monday");
			break;
	case 2:
		Console.WriteLine("Tuesday");
			break;
	case 3:
		Console.WriteLine("Wednesday");
			break;
	case 4:
		Console.WriteLine("Thursday");
			break;
	case 5:
		Console.WriteLine("Friday");
			break;
	case 6:
		Console.WriteLine("Saturday");
			break;
	case 7:
		Console.WriteLine("Sunday");
			break;	
}

// Gibt den Wochentag "Thursday" aus (Tag = 4)
```


### Das Break-Schlüsselwort

Wenn C# ein **break-Schlüsselwort** erreicht, bricht es den **switch-Block** ab.
Dadurch wird die Ausführung von weiterem Code und **Falltests** innerhalb des Blocks gestoppt.
Wenn eine Übereinstimmung gefunden wird und die Aufgabe erledigt ist, ist es Zeit für einen break. Es besteht **keine** Notwendigkeit für weitere Tests.

>[!Info]- Eine Unterbrechung (break) kann viel Ausführungszeit sparen, da sie die Ausführung des gesamten restlichen Codes im Schalterblock "ignoriert".


### Das Default-Schlüsselwort

Das **default-Schlüsselwort** ist optional und gibt einen Code an, der ausgeführt werden soll, wenn es **keine Übereinstimmung** mit den Fällen gibt:

```csharp
int day = 4;

switch (day)
{
	case 6:
		Console.WriteLine("Today is Saturday");
			break;
	case 7:
		Console.WriteLine("Today is Sunday");
			break;
	default:
		Console.WriteLine("Looking forward to the Weekend.");
			break;
}

// Gibt "Looking forward to the Weekend.", da day = 4 in default-case fällt
```



