---
aliases: 
tags:
  - foreach
  - schleifen
  - csharp
  - grundlagen
  - booleans
---
## C# Foreach Loop

Es gibt auch eine **foreach-Schleife**, die ausschließlich zum Durchlaufen von **Elementen in einem Array** (oder anderen Datensätzen) verwendet wird:

```csharp
foreach (type variableName in arrayName)
{
	// code block to be executed
}
```


Das folgende Beispiel gibt mit Hilfe der foreach-Schleife alle Elemente im Array "cars" aus:

```csharp
string[] cars = {"Volvo", "BMW", "Ford", "Mercedes"};

foreach (string i in cars)
{
	Console.WriteLine(i);
}
```