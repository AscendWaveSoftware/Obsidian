---
aliases:
  - Operatoren
tags:
  - operatoren
  - csharp
  - grundlagen
---

>[!Info]- Operatoren werden verwendet, um Operationen mit Variablen und Werten durchzuführen.


Im folgenden Beispiel wird der Operator "+" verwendet, um zwei Variablen zu addieren:
```csharp
int x = 100 + 50;
```

Der Operator "+" wird zwar häufig verwendet, um zwei Werte zu addieren, er kann aber auch verwendet werden, um eine Variable und einen Wert oder eine Variable und eine andere Variable zu addieren:
```csharp
int sum1 = 100 + 50;
int sum2 = sum1 + 250;
int sum3 = sum2 + sum2;
```




## **Arithmetische Operatoren**

| Operator | Name           | Beschreibung                             | Beispiel |
| -------- | -------------- | ---------------------------------------- | -------- |
| *+*      | Addition       | Addiert zwei Werte                       | x + y    |
| *-*      | Substitution   | Subtrahiert einen Wert von einem anderen | x - y    |
| *****    | Multiplikation | Multipliziert zwei Werte                 | x * y    |
| */*      | Division       | Dividiert einen Wert durch einen anderen | x / y    |
| *%*      | Modulus        | Gibt den Rest der Division zurück        | x % y    |
| *++*     | Increment      | Erhöht den Wert einer Variable um 1      | x++      |
| *--*     | Decrement      | Reduziert den Wert einer Variable um 1   | x--      |

## **Zuweisungsoperatoren**

Zuweisungsoperatoren werden verwendet, um Variablen Werte zuzuweisen.

Im folgenden Beispiel wird der Zuweisungsoperator "=" verwendet, um einer Variable namens "x" den Wert 10 zuzuweisen:
```csharp
int x = 10; // Zuweisung hier "="
```


| Operator | Beispiel | Anderer Ausdruck |
| -------- | -------- | ---------------- |
| *=*      | x = 5    | x = 5            |
| *+=*     | x += 5   | x = x + 5        |
| *-=*     | x -= 5   | x = x - 5        |
| ***=**   | x *= 5   | x = x * 5        |
| */=*     | x /= 5   | x = x / 5        |
| *%=*     | x %= 5   | x = x % 5        |
| *&=*     | x &= 3   | x = x & 3        |
| *\|=*    | x \|= 3  | x = x \| 3       |
| *^=*     | x ^= 5   | x = x ^ 5        |
| *>>=*    | x >>= 5  | x = x >> 5       |
| *<<=*    | x <<= 5  | x = x << 5       |


## **Vergleichsoperatoren**

Vergleichsoperatoren werden verwendet, um zwei Werte (oder Variablen) zu vergleichen. Dies ist in der Programmierung wichtig, weil es uns hilft, Antworten zu finden und Entscheidungen zu treffen.

Der Rückgabewert eines Vergleichs ist entweder wahr "**true**" oder falsch "**false**". Diese Werte sind als **boolesche Werte** bekannt.

Im folgenden Beispiel wird der **Größer-als-Operator** (>) verwendet, um herauszufinden, ob 5 größer 3 ist:
```csharp
int x = 5;
int y = 3;
Console.WriteLine(x > y); // gibt true zurück, da 5 größer 3
```



| Operator | Name                     | Beispiel |
| -------- | ------------------------ | -------- |
| **==**   | Equal to                 | x == y   |
| **!=**   | Not equal                | x != y   |
| **>**    | Greater than             | x > y    |
| **<**    | Less than                | x < y    |
| **>=**   | Greater than or equal to | x >= y   |
| **<=**   | Less than or equal to    | x <= y   |


## **Logische Operatoren**

Wie bei **Vergleichsoperatoren** kann auch mit **logischen Operatoren** der Wahrheitswert (true, false) getestet werden.

Logische Operatoren werden verwendet, um die Logik zwischen Variablen oder Werten zu bestimmen:
```csharp
int x = 5;
int y = 3;
if (x > y)
{
	Console.WriteLine("x ist größer als y");
}
```



| Operator | Name        | Beschreibung                                            | Beispiel           |
| -------- | ----------- | ------------------------------------------------------- | ------------------ |
| **&&**   | Logical and | Returns true if both statements are true                | x < 5 && x < 10    |
| **\|\|** | Logical or  | Returns true if one of the statements is true           | x < 5 \|\| x < 4   |
| **!**    | Logical not | Reverse the result, returns False if the result is true | !(x < 5 && x < 10) |
