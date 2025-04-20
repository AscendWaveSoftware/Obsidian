---
aliases: 
tags:
  - booleans
  - csharp
  - grundlagen
  - variablen
---

In der Programmierung benötigt man oft einen [[Datentypen]], der nur einen von zwei Werten annehmen kann, wie z. B.:

**Ja / Nein**
**Ein / Aus**
**Wahr / Falsch**

Hierfür gibt es in **C#** den Datentyp **bool**, der die Werte **true** oder **false** annehmen kann.
Ein **boolescher** Typ wird mit dem Schlüsselwort **bool** deklariert und kann nur die Werte true oder false annehmen:

```csharp
bool isActive = true;
bool isAvailable = false;
Console.WriteLine(isActive); // Outputs True
Console.WriteLine(isAvailable); // Outputs False
```

>[!Info]- Üblicher ist es jedoch, boolesche Werte aus booleschen Ausdrücken zurückzugeben, um bedingte Tests durchzuführen.


## **Boolescher Ausdruck**

Ein **boolescher Ausdruck** gibt einen booleschen Wert zurück: Wahr oder Falsch, durch den Vergleich von **Werten/Variablen**.
Dies ist nützlich, um eine Logik aufzubauen und Antworten zu finden.

Im folgenden Beispiel wird der Vergleichsoperator **größer als (>)** verwendet, um herauszufinden, ob ein Ausdruck (oder eine Variable) wahr ist: 

```csharp
int x = 10;
int y = 9;
Console.WriteLine(x > y); // Output wäre hier True, da x größer als y
```

>[!Info]- Gleiche Bedeutung:
```csharp
Console.WriteLine(10 > 9);
```



In den folgenden Beispielen wird der Operator **equal to** verwendet, um einen Ausdruck auszuwerten:

```csharp
int x = 10;
Console.WriteLine(x == 10); // True

Console.WriteLine(x == 15); // False
```


### **Beispiel**:

Ausgabe "Alt genug zu wählen!", wenn **myAge** größer oder gleich **18** ist. Andernfalls wird "Nicht alt genug zum Wählen." ausgegeben:

```csharp
int myAge = 26;
int votingAge = 18;

if (myAge >= votingAge) 
{
	Console.WriteLine("Alt genug zu wählen!");
}
else 
{
	Console.WriteLine("Nicht alt genug zum Wählen.");
}
```