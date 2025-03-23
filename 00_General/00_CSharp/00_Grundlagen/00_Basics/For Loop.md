---
aliases: 
tags:
  - for
  - schleifen
  - csharp
  - grundlagen
---
## C# For Loop

Wenn man genau weiß, wie oft ein Codeblock in einer Schleife durchlaufen soll, wird die **for-Schleife** anstelle der **while-Schleife** verwendet:

```csharp
for (statement 1; statement 2; statement 3) 
{
	// code block to be executed
}
```


**Statement 1** wird (einmalig) vor der Ausführung des Codeblocks ausgeführt.
**Statement 2** definiert die Bedingung für die Ausführung des Codeblocks.
**Statement 3** wird (jedes Mal) ausgeführt, nachdem der Codeblock ausgeführt wurde.


Das folgende Beispiel gibt die Zahlen 0 bis 4 aus:

```csharp
for (int i = 0; i < 5; i++)
{
	Console.WriteLine(i);
}
```

**Erklärung**: Statement 1 **setzt** eine Variable, bevor die Schleife beginnt (int i = 0). Statement 2 **definiert** die Bedingung für den Schleifendurchlauf (i muss kleiner als 5 sein). Wenn die Bedingung wahr ist, beginnt die Schleife von vorne, wenn sie falsch ist, wird die Schleife beendet. Statement 3 **erhöht** einen Wert (i++) jedes Mal, wenn der Codeblock in der Schleife ausgeführt wurde.


Ein weiteres Beispiel:

```csharp
// Gibt nur gerade Werte zwischen 0 und 10 an
for (int i = 0; i < 10; i = i + 2)
{
	Console.WriteLine(i);
}
```


### Verschachteltet Schleifen (Nested Loops)

Es ist auch möglich, eine Schleife innerhalb einer anderen Schleife zu platzieren. Dies wird als geschachtelte Schleife bezeichnet.
Die **innere Schleife** wird bei jeder **Iteration** der **äußeren Schleife** ein Mal ausgeführt:

```csharp
// Outer Loop
for (int = 1; i < 2; i++)
{
	Console.WriteLine("Outer: " + i); // Executes 2 times

	for (int j = 1; j <= 3; j++)
	{
		Console.WriteLine("Inner: " + j); // Executes 6 times (2 * 3)
	}
}

/* Output:
	Outer: 1
		Inner: 1
		Inner: 2
		Inner: 3
	Outer: 2
		Inner: 1
		Inner: 2
		Inner: 3 /*
```