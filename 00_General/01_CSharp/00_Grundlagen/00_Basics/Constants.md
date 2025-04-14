---
aliases:
  - Konstanten
tags:
  - const
  - csharp
  - grundlagen
  - variablen
---

>[!Info]- Wenn ein vorhandener Wert zur Laufzeit des Programm nicht überschrieben werden soll, kann das Schlüsselwort *const* vor den Variablentyp gesetzt werden. Dadurch wird die Variable "konstant" deklariert, d. h. unveränderlich und schreibgeschützt.


**Beispiel:**
```csharp
const int myNum = 15;
myNum = 20; // Würde einen Error verursachen
```


Das Schlüsselwort **const** ist nützlich, wenn man möchte, dass eine Variable immer denselben Wert speichert, damit andere (oder man selbst) den Code nicht durcheinanderbringen. Ein Beispiel, das oft als Konstante bezeichnet wird, ist **PI** (3.14159...).


>[!Note]- **Hinweis**: Eine konstante Variable kann nicht deklariert werden, ohne den Wert zuzuweisen. Wenn das geschieht, tritt ein Error auf: Für ein const-Feld muss ein Wert angegeben werden.

