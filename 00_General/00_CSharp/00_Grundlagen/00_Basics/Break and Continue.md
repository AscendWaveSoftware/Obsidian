---
aliases: 
tags:
  - break
  - continue
  - schleifen
  - csharp
  - grundlagen
---
## C# Break

Das **Break-Statement** wird verwendet, um aus einer **switch-Anweisung** "herauszuspringen".
Die break-Anweisung kann auch verwendet werden, um aus einer Schleife herauszuspringen.

In folgendem Beispiel wird die Schleife verlassen, wenn i gleich 4 ist:

```csharp
for (int i = 0; i < 10; i++)
{
	if (i == 4)
	{
		break;
	}
	Console.WriteLine(i);
}
```


## C# Continue

Die **continue-Anweisung** bricht eine Iteration (in der Schleife) ab, wenn eine bestimmte Bedingung eintritt und fährt mit der nächsten Iteration in der Schleife fort.

In folgendem Beispiel wird der Wert von 4 übersprungen:

```csharp
	for (int i = 0; i < 10; i++)
{
	if(i == 4)
	{
		continue;
	}
	Console.WriteLine(i);
}
```


### Break & Continue in einem While Loop

**Break & Continue** können auch in einem **while-Loop** verwendet werden:

```csharp
int i = 0;

while (i < 10)
{
	Console.WriteLine(i);
	i++;
	if(i == 4)
	{
		break;
	}
}
```


```csharp
int i = 0;

while (i < 10)
{
	if (i == 4)
	{
		i++;
		continue;
	}
	Console.WriteLine(i);
	i++;
}
```