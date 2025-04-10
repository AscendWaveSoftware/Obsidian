---
aliases: 
tags:
  - listen
  - csharp
  - grundlagen
---

## Was ist eine Liste

Eine Liste **"List<>"** ist eine dynamische Datenstruktur, die mehrere Elemente vom selben Datentyp speichert. Anders als Arrays können Listen ihre Größe dynamisch verändern (Elemente hinzufügen, entfernen, sortieren, etc.).

>[!Info]- Bestandteil des Namespaces: **using** System.Collections.Generics;

```csharp
// Definition einer Liste mit Datentyp T
List<int> zahlenListe = new List<int>();

// Mit Initialisierung
List<string> namen = new List<string> { "Anna", "Samuel", "Lisa" };
```

#### Elemente hinzufügen:

```csharp
zahlenListe.Add(10); // {10}
zahlenListe.Add(20); // {10, 20}

// mehrere Elemente auf einmal hinzufügen
zahlenListe.AddRange(new int[] {30, 40}); // {10, 20, 30, 40}

// Element an bestimmter Position
zahlenListe.Insert(1, 15); // {10, 15, 20, 30, 40}
```

#### Elemente entfernen:

```csharp
// Erstes Vorkommen eines Elements
zahlenListe.Remove(20); // {10, 15, 30, 40}

// Element an bestimmtem Index entfernen
zahlenListe.RemoveAt(2); // {10, 15, 40}

// Alle Elemente entfernen
zahlenListe.Clear(); // {}
```

#### Element abrufen:

```csharp
string ersterName = namen[0]; // "Anna"
```

#### Elemente durchlaufen (Iterieren)

```csharp
foreach(string name in namen)
{
	Console.WriteLine(name);
}

// Mit for-Schleife
for(int i = 0; i < namen.Count; i++)
{
	Console.WriteLine(namen[i]);
}
```


### Eigenschaften (Properties)

| **Eigenschaft** | **Beschreibung**                                                                    |
| --------------- | ------------------------------------------------------------ |
| **.C                                                   Anzahl der möglichen Elemente (Speicherplatz vorreserviert)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  t)  |
```csharp
int anzahl = namen.Count; // z. B. 3
```


### Nützliche Methoden im Überblick

| **Methode**                   | **Beschreibung**                                 |
| ----------------------------- | ------------------------------------------------ |
| **Add(T item)**               | Fügt ein Element am Ende hinzu                   |
| **AddRange(IEnumerable<>)**   | Fügt mehrere Elemente hinzu                      |
| **Insert(int Index, T item)** | Fügt Element an bestimmter Stelle hinzu          |
| **Remove(T item)**            | Entfernt das erste Vorkommen eines Elements      |
| **RemoveAt(int Index)**       | Entfernt Element an bestimmter Stelle            |
| **Clear()**                   | Entfernt alle Elemente                           |
| **Contains(T item)**          | Prüft, ob ein Element enthalten ist (true/false) |
| **IndexOf(T item)**           | Gibt den Index eines Elements zurück             |
| **Sort()**                    | Sortiert die Liste aufsteigend                   |
| **Reverse()**                 | Kehrt die Reihenfolge der Elemente um            |
| **ToArray()**                 | Wandelt Liste in Array um                        |



>[!Warning]- Performance Tipp: Nutze **Capacity**, wenn du die finale Größe einer Liste vorher kennst, um Speicher zu optimieren.

```csharp
List<int> liste = new List<int>(1000); // Speicherplatz vorreserviert
```


### Unterschied Liste vs. Array

| **Merkmal**                | **Array**                 | **Liste**                         |
| -------------------------- | ------------------------- | --------------------------------- |
| **Größe**                  | Fest definiert (statisch) | Dynamisch erweiterbar             |
| **Geschwindigkeit**        | Schnell bei fester Größe  | Flexibler bei dynamischer Größe   |
| **Speicherplatzverbrauch** | Gering                    | Höher durch dynamische Verwaltung |
| **Einsatzgebiet**          | Feste Anzahl Elemente     | Variable Anzahl von Elementen     |

