---
aliases: 
tags:
  - if-else-statements
  - csharp
  - grundlagen
  - booleans
  - elseif
---
## C#-Bedingungen und If-Statements

C# unterstützt die üblichen logischen Bedingungen aus der Mathematik:
- **Kleiner als: a < b**
- **Kleiner als oder gleich: a <= b**
- **Größer als: a > b**
- **Größer als oder gleich: a >= b
- **Gleich: a == b
- **Nicht gleich: a != b

Diese Bedingungen können verwendet werden, um verschiedene Aktionen für verschiedene Entscheidungen durchzuführen.

C# hat die folgenden bedingten Anweisungen:
- Verwende **if**, um einen Codeblock anzugeben, der ausgeführt werden soll, wenn eine bestimmte Bedingung erfüllt ist.
- Verwende **else**, um einen Codeblock anzugeben, der ausgeführt werden soll, wenn die gleiche Bedingung falsch ist.
- Verwende **else if**, um eine neue Bedingung anzugeben, die getestet wird, wenn die erste Bedingung falsch ist.
- Verwende **switch**, um mehrere alternative Codeblöcke anzugeben, die ausgeführt werden sollen.

### If-Statement

Verwende die **if-Anweisung**, um einen Block von C#-Code anzugeben, der ausgeführt wird, wenn eine Bedingung **wahr** ist:

```csharp
if (condition)
{
	// block of code to be executed if the condition is True
}
```

>[!Info]- Beachte, dass if in **Kleinbuchstaben** geschrieben wird. Großbuchstaben (If oder IF) führen zu einem Fehler.

**Beispiel**:
```csharp
int x = 20;
int y = 10;

if (x > y)
{
	Console.WriteLine("x ist größer als y");
}
```


### Else-Statement

Verwende die **else-Anweisung**, um einen Codeblock anzugeben, der ausgeführt wird, wenn die Bedingung **falsch** ist:

```csharp
if (condition)
{
	// block of code to be executed if the condition is True
}
else
{
	// block of code to be executed if the condition is False
}
```


**Beispiel**:
```csharp
int time = 20;

if (time < 18)
{
	Console.WriteLine("Good day.");
}
else 
{
	Console.WriteLine("Good evening.");
}

// Hier wird "Good evening" ausgegeben, da time > 18
```


### Else If Statement

Verwende die **else if-Anweisung**, um eine neue Bedingung anzugeben, wenn die erste Bedingung falsch ist:

```csharp
if (condition1)
{
	// block of code to be executed if the condition is True
}
else if (condition2)
{
	// block of code to be executed if the condition1 is false and condition2 is          True
}
else
{
	// block of code to be executed if the condition1 is false and condition2 is          False
}
```


**Beispiel**:
```csharp
int time = 20;

if (time < 10)
{
	Console.WriteLine("Good morning.");
}
else if (time < 20) 
{
	Console.WriteLine("Good day.");
}
else 
{
	Console.WriteLine("Good evening.");
}

// Hier wird "Good evening." ausgegeben, da time >= 20
```