---
aliases: 
tags:
  - aufgaben
  - übung
  - csharp
  - grundlagen
---
## Benutzung von Schleifen in Kombination mit "%"

**Aufgabe**: **Gerade Zahlen von 1 bis 50**
Gib nur die Zahlen zwischen 1 und 50 aus. Verwende **continue**, um ungerade Zahlen zu überspringen:

```csharp
for (int i = 1; i <= 50; i++)
{
	if (i % 2 != 0)
	{
		continue;
	}
	Console.WriteLine(i);
}
```


## Schleifen

**Aufgabe**: **Benutzereingabe bis "exit"**
Nutze eine **while**-Schleife, um immer wieder Benutzereingaben zu lesen. Das Programm soll erst enden, wenn der Nutzer "exit" eintippt. **Ergänzung**: Zähle zusätzlich, wie oft der Benutzer etwas eingegeben hat, bevor exit geschrieben wurde: 

```csharp
string userInput = "";
int inputs = 0;


while (userInput.toLower != "exit")
{
	Console.WriteLine("Bitte gebe 'exit' ein, um das Programm zu beenden.");
	inputs++;
	userInput = Console.Readline();
}
Console:WriteLine($"Das Programm wurde erfolgreich mit {inputs} Inputs beendet.");
```


**Aufgabe**: **Summe aller Zahlen in einem Array**
Verwende einen **foreach**-Schleife, um ein int-Array zu durchlaufen und die Summe aller Zahlen zu berechnen:

```csharp
int[] numbers = {5, 6, 2, 9, 4};
int sum = 0;

foreach (int i in numbers)
{
	sum += i;
}
Console.WriteLine("Die Summe aller Zahlen beträgt: " + sum);
```


**Aufgabe**: **Erstes Vorkommen einer bestimmten Zahl**
Durchlaufe ein Array mit einer **for**-Schleife und finde das erste Vorkommen einer bestimmten Zahl z. B. 42. Brich die Schleife mit **break** ab, wenn du sie gefunden hast:

**Ansatz ohne vordefiniertes Array**
```csharp
for (int i = 0; i <= 100; i++)
{
	Console.WriteLine(i);
	if (i == 42)
	{
		Console.WriteLine("Die Zahl 42 gefunden. Schleife bricht ab.");
		break;
	}
}
```

**Ansatz mit vordefinierten Array
```csharp
int[] numbers = { 5, 13, 8, 42, 99, 3};

for (int i = 0; i < numbers.Length; i++) 
{
	if (numbers[i] == 42) 
	{
		Console.WriteLine($"Die Zahl 42 an Index {i} gefunden.");
		break;
	}
}
```


**Aufgabe**: **Kleines Zahlenspiel**
Lasse den Benutzer eine Zahl zwischen 1 und 10 erraten.
Solange er falsch liegt, soll er erneut raten.
Wenn er richtig rät, gib aus: "Richtig!" und beende die Schleife mit **break**.

```csharp
 Random rnd = new Random();
 int numberToGuess = rnd.Next(1, 10 + 1);
 int userGuess = 0;
 int guesses = 0;

 while (userGuess != numberToGuess)
 {
     Console.Write("Bitte gebe ein Zahl zwischen 1-10 ein: ");
     int.TryParse(Console.ReadLine(), out userGuess);
     if (userGuess <= 0 || userGuess > 10)
     {
         Console.WriteLine("Ungültige Eingabe!");
         continue;
     }

     guesses++;

     if (userGuess < numberToGuess)
     {
         Console.WriteLine($"Die Zahl ist größer als {userGuess}.");
     }
     else if (userGuess > numberToGuess)
     {
         Console.WriteLine($"Die Zahl ist kleiner als {userGuess}.");
     }
     else
     {
         Console.WriteLine($"Richtig! Die Zahl war {numberToGuess}.");
         Console.WriteLine($"Du hast {guesses} Versuche gebraucht.");
         break;
     }
 }
```

