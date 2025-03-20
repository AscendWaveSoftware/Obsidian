---
aliases:
  - Variablen
tags:
  - datentypen
  - variablen
  - csharp
  - grundlagen
---


>[!info]- **Variablen** sind das wichtigste Konzept in der gesamten Programmierwelt, denn in Variablen kann man zur Laufzeit von einem Programm Daten speichern und diese Daten in dem Code weiterverwenden. So kann man Variablen auch als **Speicherplatz für Daten** bezeichnen, welcher während der Laufzeit eines Programms existiert. Der Wert der Variable kann während der Programmlaufzeit verändert werden. Die Variable fungiert wie ein Platzhalter und steht bei der Verwendung der Variable immer für jenen Wert, der ihr zugewiesen wurde




>[!info]- Wie definiere ich eine Variable?
>Zuallererst wird der Datentyp angegeben. In C# gibt es verschiedene Datentypen - je nachdem, welche Werte in der Variable gespeichert werden sollen. Dann wird der Variable ein Name gegeben. Dieser sollte den Inhalt der Variable möglichst gut beschreiben. Die Deklarierung einer Variable schließt immer mit einem Komma (Semikolon).<br><br>Datentyp Variablenname = Inhalt;




>[!Info]- Deklarierung und Initialisierung einer Variable
>Bei der Arbeit mit Variablen muss man zwischen zwei Prinzipien unterscheiden - zwischen der **Deklarierung und Initialisierung**. Bei der Deklarierung einer Variable wird einer Variable ein Wert zugewiesen. Dazu gibt man den Datentyp und Namen an und schließt mit einem Semikolon. Ein Wert kann zu einem späteren Zeitpunkt hinzugefügt werden.<br>**Beispiel:** int alter;<br><br>Bei der **Initialisierung** gibt man der Variable mit der Deklarierung auch direkt eine Wertzuweisung.<br>**Beispiel:** int alter = 26;




>[!Info]- Arten von Datentypen

| Datentyp    | Beschreibung                                                                                                                                                                                                                                       |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **char**    | In einem Char kann man einzelne Unicode-Zeichen speichern. Diese werden von einfachen Hochkomma umgeben.                                                                                                                                           |
| **string**  | Ein String (Zeichenfolge) besteht aus mindestens zwei Zeichen. Der Text innerhalb der Variable wird immer mit Hochkomma umgeben. Alles innerhalb der Hochkomma wird als Text interpretiert.                                                        |
| **integer** | Mit dem Datentyp Integer können Zahlen gespeichert werden. Int ist dabei eigentlich nur eine Abkürzung für Int32. Mit Int32 kannst du Zahlen im Bereich von -2.147.483.648 bis 2.147.483.647 aufnehmen. Ein Integer kann nur Ganzzahlen aufnehmen. |
| **float**   | Der Datentyp Float wird wie auch der Datentyp Int dazu verwendet, um Zahlen zu speichern. Im Unterschied zu Int kann Float aber auch mit Gleitkommazahlen arbeiten. Ein Float kann bis zu sieben Nachkommazahlen speichern.                        |
| **bool**    | Der Datentyp bool kann nur zwei Werte speichern. Wahr und falsch. Dieser Datentyp wird oft im Zusammenhang mit IF-Statements verwendet.                                                                                                            |
| **uint**    | Eine positive Ganzzahl von 0 bis 4.294.967.295                                                                                                                                                                                                     |
| **double**  | Eine Kommazahl. 1.7E +/- 308 (15 Ziffern)                                                                                                                                                                                                          |
| **long**    | Eine Ganzzahl von -2.147.483.648 bis 2.147.483.647                                                                                                                                                                                                 |
| **ulong**   | Eine positive Ganzzahl von 0 bis 4.294.967.295                                                                                                                                                                                                     |
| **short**   | Eine Ganzzahl von -32.768 bis 32.767                                                                                                                                                                                                               |
| **ushort**  | Eine positive Ganzzahl von 0 bis 65.535                                                                                                                                                                                                            |
| **byte**    | Ein 8-bit uint von 0 bis 255                                                                                                                                                                                                                       |
| **sbyte**   | Ein 8-biz uint type von -128 bis 127                                                                                                                                                                                                               |


>[!Info]- Beispiele

```csharp
char x = 'x';

string name = "Sammy";

int alter = 26;

float kommazahl = 14.6532;

bool on = false;

uint ganzzahl = 924;

double x = 15.1415;

long y = 256234;

ulong value = 652367;

short damage = 6556;

ushort value = 3452;

byte bit = 255;

sbyte sbit = 123;
```