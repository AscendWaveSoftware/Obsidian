---
aliases:
  - Collection
tags:
  - array
  - csharp
  - grundlagen
  - variablen
---

>[!Info]- Was ist ein Array?
>Ein **Array** wird genutzt um mehrere Werte in einer einzelnen Variable zu speichern, anstatt mehrere Variablen zu deklarieren.
>


```csharp
string[] cars;

string cars = {"Volvo,", "BMW", "Ford", "Mazda"};

int[] myNum = {10, 20, 30, 40};


// Access the Elements of an Array
string[] cars = {"Volvo", "BMW", "Mercedes"};
Console.WriteLine(cars[0]); // Output Volvo

Console.WriteLine(cars.Length); // Output alle Werte im Array


// Alternative Wege ein Array zu erstellen
string[] cars = new string[4];

string[] cars = new string[4] {"Volvo", "Mercedes", "BMW"};
```