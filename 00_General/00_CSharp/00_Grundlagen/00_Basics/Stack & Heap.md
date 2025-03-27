---
aliases: 
tags:
  - stack
  - heap
  - daten
  - speicher
  - csharp
  - grundlagen
---

## Stack vs. Heap

In C# werden Daten im Speicher grundsätzlich auf zwei Arten abgelegt: 

1. **Stack** (Stapel)
2. **Heap** (Haufen)

**Beide sind Speicherbereiche**, die sich jedoch stark unterscheiden:


| Merkmal              | Stack                                            | Heap                                                   |
| -------------------- | ------------------------------------------------ | ------------------------------------------------------ |
| **Speicherstruktur** | Organisiert (Last-In-First-Out)                  | Unorganisiert (dynamische Größe)                       |
| **Zugriffszeit**     | Sehr schnell (effizienter Zugriff)               | Etwas langsamer (flexibel)                             |
| **Größe**            | Klein und begrenzt                               | Groß und nahezu unbegrenzt                             |
| **Verwaltung**       | Automatisch vom System verwaltet                 | Manuelle & automatische Verwaltung (Garbage Collector) |
| **Datenart**         | Werttypen (struct, int, bool, etc.) & Referenzen | Referenztypen (class, object, array, etc.)             |
| **Lebensdauer**      | Kurzlebig, lokal innerhalb einer Methode         | Langfristig, Objekte leben länger                      |


### Stack im Detail

Der **Stack** ist ein Speicherbereich, der nach dem LIFO-Prinzip (**Last In First Out**) funktioniert.

- Bei jedem Methodenaufruf legt das System automatisch einen sogenannten **Stack Frame** an.
- Innerhalb dieses Frames werden **lokale Variablen** und **Werttypen** gespeichert.
- Sobald die Methode beendet ist, werden alle Daten auf dem Stack wieder entfernt.

```csharp
void MyMethod()
{
	int number = 10; // landet auf dem Stack
	int result = number * 2; // ebenfalls Stack
} // am Ende der Methode wird alles vom Stack entfernt
```

>[!info]- Variablen (int, double, structs) landen hier direkt. Sehr effizient, da kein komplexes Management nötig ist.



### Heap im Detail

Der **Heap** ist ein Speicherbereich für Daten, die **länger leben** oder deren Größe nicht vorher feststeht.

- Der Heap speichert **Referenztypen** wie Klassen-Instanzen, Objekte und Arrays.
- Wird dynamisch verwaltet (keine feste Reihenfolge, fragmentiert möglich).
- Daten auf dem Heap müssen explizit mit **new** erzeugt werden.
- Aufräumen übernimmt der Garbage Collector automatisch, wenn keine Referenzen mehr vorhanden sind.

```csharp
class Person
{
	public string Name;
	public int Age;
}

void MyMethod()
{
	Person A = new Person(); // Objekt landet auf dem Heap
	p.Name = "Sammy";
	p.Alter = 26;
} // referenz "p" wird entfernt, Objekt wird später vom Garbage Collector gelöscht
```

>[!info]- p selbst ist auf dem **Stack**, aber die **Objektdaten** (Name, Alter) befinden sich auf dem **Heap**


### Zusammenfassung Stack & Heap


![[Screenshot (101).png]]

- **Stack** speichert die **Referenz** auf das Objekt (Heap).
- **Heap** speichert die **Objektdaten** selbst.


### Unterschiedliche Verhaltensweisen (Werttyp vs. Referenztyp)

**Werttypen (struct, int, bool)**:

- Liegen meist direkt auf dem **Stack**
- Werden beim Kopieren komplett kopiert.

```csharp
int a = 5;
int b = a; // Kopie
b = 10;

Console.WriteLine(a); // 5
Console.WriteLine(b); // 10
```


**Referenztypen (class, object, array)**:

- Liegen auf dem **Heap**, die Referenz darauf liegt auf dem Stack.
- Beim Kopieren wird nur die Referenz kopiert, beide Variablen zeigen auf das gleiche Objekt.

```csharp
class Example { public int Value; }

Example a = new Example { Value = 5 };
Example b = a; // Referenz kopiert!
b.Value = 10;

Console.WriteLine(a); // 10
Console.WriteLine(b); // 10
```


>[!warning]- Performance-Aspekte
> - Stack **sehr schnell** (automatisches, effizientes Handling).
> - Heap **langsamer**, da der Garbage Collector regelmäßig arbeitet und den Speicher aufräumt.



### Speicherverwaltung

Beim Stack wird der Speicher **automatisch freigegeben**, wenn eine Methode endet. Man muss sich dabei um nichts kümmern.

Beim Heap sucht und entfernt der **Garbage Collector** automatisch unbenutzte Objekte. Das kann nicht direkt gesteuert werden, aber man kann Objekte bewusst auf **null** setzen, um sie freizugeben:

```csharp
Person p = new Person();
// ... verwende p
p = null; // Objekt kann jetzt durch Garbage Collector entfernt werden
```



### Wann wird der Heap und wann der Stack bevorzugt

**Heap**:

- Komplexe Objekte (Klasseninstanzen, Arrays, Collections)
- Dynamische Objekte, deren Größe sich verändern kann
- Wenn du Objekte über mehrere Methoden hinweg weitergeben möchtest

**Stack**:

- Kurze Lebensdauer der Daten (lokale Variablen)
- Werttypen (Structs, ints, bools)
- Hohe Performance für einfache Variablen benötigt



#### Wichtige Hinweise für die Praxis

>[!warning]- **Stack Overflow**: Wenn der Stack zu groß wird (z. B. bei Rekursion), tritt ein **StackOverflowException** auf.


>[!warning]- **Heap-Speicherprobleme**: Bei unvorsichtigem Umgang können viele Heap-Objekte den Speicher belasten und zu höherem Aufwand beim Garbage Collector führen.



## Fazit


| **Stack**                           | **Heap**                                    |
| ----------------------------------- | ------------------------------------------- |
| Werttypen & Referenzen              | Referenztypen                               |
| Schnell, klein, automatisch         | Flexibel, groß, Garbage Collection          |
| Lokale Variablen, kurze Lebensdauer | Objekte, Klassen, Arrays, lange Lebensdauer |
