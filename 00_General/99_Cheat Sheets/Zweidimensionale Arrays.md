---
aliases: 
tags:
  - zweidimensionalearrays
  - cheatsheet
  - csharp
  - grundlagen
  - array
---
## Was ist ein Array

Ein **Array** ist eine Datenstruktur, die mehrere Werte desselben Typs in einer einzigen Variable speichert.

```csharp
int[] numbers = new int[5]; // Array mit 5 Elementen
```


## Was ist ein zweidimensionales Array

Ein **zweidimensionales Array** kann man sich wie eine Tabelle mit Zeilen und Spalten vorstellen. Es hat also zwei **Indizes**:

- **Erster Index**: Reihe (Zeile)
- **Zweiter Index**: Spalte

```csharp
int[,] table = new int[3,4]; // 3 Zeilen, 4 Spalten
```


>[!warning]- So sieht ein 2D-Array visuell aus (3x4):


|     | 0     | 1     | 2     | 3     |
| --- | ----- | ----- | ----- | ----- |
| 0   | [0,0] | [0,1] | [0,2] | [0,3] |
| 1   | [1,0] | [1,1] | [1,2] | [1,3] |
| 2   | [2,0] | [2,1] | [2,2] | [2,3] |

**Um auf ein Element zuzugreifen oder ihm einen Wert zuzuweisen**:

```csharp
table[1,2] = 7;
```


### Durchlaufen eines zweidimensionalen Arrays

Dazu werden verschachtelte Schleifen (eine äußere Schleife für Zeilen, eine innere Schleife für Spalten):

```csharp
for(int zeile = 0; zeile < 3; zeile++)
{
	for(int spalte = 0; spalte < 4; spalte++)
	{
		Console.Write("table[zeile, spalte] + " ");
	}
	Console.WriteLine();
}
```