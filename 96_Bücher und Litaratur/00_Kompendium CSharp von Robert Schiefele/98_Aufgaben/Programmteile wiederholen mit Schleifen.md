---
aliases: 
tags:
  - kompendium
  - csharp
  - robertschiefele
  - aufgaben
  - übung
  - schleifen
---

**Aufgabe: Schreiben Sie ein Programm, das eine Textzeile nach der anderen von der Tastatur einliest. Wenn der Benutzer die Textzeile "Fertig!" eingibt, soll das Programm eine Zeile mit 10 Sternchen ausgeben und dann den gesamten eingegebenen Text, aber ohne die Zeile "Fertig!".

```csharp
               // Hier wird der eingegebene Text gespeichert
               var text = "";

               // Command zum Beenden der Schleife
               var fertig = "Fertig!";

               // Aktueller Input
               var eingabe = "";

               // Schleife läuft, solange nicht fertig eingegeben wird
               while ((eingabe = Console.ReadLine()) != fertig)
               {
                   // Zum Text wird die aktuelle Eingabe hinzugefügt
                   text += eingabe;
                   // Und anschließend ein Zeilenumbruch hinzugefügt
                   text += "\r\n";
               }

               // Hier werden beim Beenden 10 Sternchen ausgegeben
               Console.WriteLine("**********");

               // Wird splitten unsere Zeilen über \r\n
               var zeilen = text.Split("\r\n");

               foreach (var zeile in zeilen)
               {
  // solange die Zeile nicht fertig beinhaltet, wird diese in der Konsole ausgegeben
                   if (zeile != fertig)
                   {
                       Console.WriteLine(zeile);
                   }
               } 
```


**Aufgabe: Schreiben Sie ein Programm, das mit Hilfe eines Arrays ein Dreieck aus Sternchen-Zeichen ausgibt.**

```csharp
 int[] zahlen = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

 foreach (var zahl in zahlen)
 {
     for (var i = 0; i < zahl; i++)
     {
         for (int j = 1; j == j * 2 - 1; j++)
         {
             Console.Write(' ');
         }
         Console.Write('*');
     }


     Console.WriteLine();
 }
```

