---
aliases: 
tags:
  - while
  - schleifen
  - csharp
  - grundlagen
  - booleans
---
## C# While-Loop

### Schleifen

**Schleifen** können einen Codeblock so lange ausführen, bis eine bestimmte Bedingung erfüllt ist.
Schleifen sind praktisch, weil sie Zeit sparen, Fehler reduzieren und den Code besser lesbar machen.

Die **while-Schleife** durchläuft einen Codeblock so lange, wie eine bestimmte Bedingung erfüllt ist:

```csharp
while (condition) 
{
	// code block to be executed
}
```

In folgendem Beispiel läuft die Schleife solange **i** kleiner als 5 ist:

```csharp
int i = 0;
while (i < 5)
{
	Console.WriteLine("i");
	i++;
}

// Würde die Werte 0, 1, 2, 3, 4 ausgeben und die Schleife dann verlassen
```

>[!Info]- In diesem Beispiel darf nicht vergessen werden die Variable **i** zu erhöhen (i++), da die Schleife sonst nie beendet werden würde.


## Die Do/While-Schleife

Die **do/while-Schleife** ist eine Variante der **while-Schleife**. Diese Schleife führt den Codeblock **einmal** aus, bevor sie prüft, ob die Bedingung erfüllt ist und wiederholt dann die Schleife, solange die Bedingung erfüllt ist.

```csharp
do 
{
	// code block to be executed
}
while (condition);
```


Im folgenden Beispiel wird eine do/while-Schleife verwendet. Die Schleife wird immer mindestens einmal ausgeführt, auch wenn die Bedingung falsch ist, da der Codeblock ausgeführt wird, bevor die Bedingung getestet wird:

```csharp
int i = 0;
do 
{
	Console.WriteLine(i);
	i++;
}
while (i < 5);
```