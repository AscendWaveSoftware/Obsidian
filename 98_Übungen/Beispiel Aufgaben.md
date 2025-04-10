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


## Zweidimensionale Arrays

**Aufgabe: Grundlagen**
Erstelle ein 4x4 großes Array. Fülle jede Zelle mit Zahlen, die der Summe ihrer Koordinaten entsprechen. Gib das Array vollständig auf der Konsole aus.

```csharp
char[,] myArray = new char[4,4];

for(int i = 0; i < 4; i++)
{
	for(int j = 0; j < 4; j++)
	{
		int sum = i + j;
		Console.Write(sum);
	}
	Console.WriteLine();
}
```


**Aufgabe: Muster erstellen**
Erstelle ein 5x5 Array. Platziere "X" an den Rändern und "O" im Innenbereich.

```csharp
char[,] myArray = new char[5,5];

for(int i = 0; i < 5; i++)
{
	for(int j = 0; j < 5; j++)
	{
		if(i == 0 || i == 4 || j == 0 || j == 4)
		{
			Console.Write('X');
		}
		else
		{
			Console.Write('O');
		}
	}
	Console.WriteLine();
}
```


**Aufgabe: Ein Element suchen**
Erstelle ein 3x3 Array mit zufälligen Zahlen von 1 bis 9. Schreibe ein Programm, das eine Zahl eingibt und sagt, ob sie im Array existiert und wenn ja, an welcher Position sie ist.

```csharp
Random rnd = new Random();

int[,] myArray = new int[3, 3];

for (int i = 0; i < myArray.GetLength(0); i++)
{
    for(int j = 0; j < myArray.GetLength(1); j++)
    {
        myArray[i, j] = rnd.Next(1, 10 + 1);
    }
}

// Array ausgeben
for (int i = 0; i < myArray.GetLength(0); i++)
{
    for (int j = 0; j < myArray.GetLength(1); j++)
    {
        Console.Write(myArray[i, j] + " ");
    }
    Console.WriteLine();
}

int input = 0;
bool validInput = false;


do
{
    Console.WriteLine("Bitte gib eine  Ganzzahl ein.");
    
    if(int.TryParse(Console.ReadLine(), out input))
    {
        validInput = true;
    }
    else
    {
        Console.WriteLine("Ungültige Eingabe!");
    }

} while (!validInput);


for (int i = 0; i < myArray.GetLength(0); i++)
{
    for (int j = 0; j < myArray.GetLength(1); j++)
    {
        if (input == myArray[i, j])
        {
            Console.WriteLine($"{input} ist im Array an Stelle [{i + 1}, {j + 1}] enthalten!");
            return;
        }
    }
}

Console.WriteLine($"Die Zahl {input} ist nicht im Array enthalten.");
```



