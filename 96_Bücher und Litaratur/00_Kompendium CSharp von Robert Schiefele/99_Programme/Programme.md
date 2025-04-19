---
aliases: 
tags:
  - übung
  - programme
  - textsuche
  - csharp
  - schleifen
  - split
---

## Programmteile wiederholen mit Schleifen

**Progamm: Ein String-Array "text" wird aufgebrochen und nach einem Suchbegriff durchsucht**

```csharp
var text = "Das Buch C# Kompendium ist ein Buch zum Erlernen von C#. Geschrieben hat das Buch Robert Schiefele";

var suchbegriff = "Buch";

var wortGefunden = false;
var wortInZeile = 0;
var wortIstAnPosition = 0;

var zeilen = text.Split("\r\n");
for (var i = 0; i < zeilen.Length; i++)
{
    var woerter = zeilen[i].Split(" ");
    for (var j = 0; j < woerter.Length; j++)
    {
        if (!wortGefunden)
        {
            if (woerter[j] == suchbegriff)
            {
                wortInZeile = i + 1;
                wortIstAnPosition = j + 1;
                wortGefunden = true;
				break;
            }
        }
    }
    if(wortGefunden)
	    break;
}
Console.WriteLine($"Der Begriff {suchbegriff} befindent sich in Zeile: {wortInZeile} an Position: {wortIstAnPosition}.");
```


**Prgramm: Einfache Ausgabe eines Tic-Tac-Toe Spielfeldes mit einem 2-dimensionalen Array.**

```csharp
var spielfeld = new string[4, 4]
{   {" ", "A", "B", "C"},
    {"1", "#", "#", "#"},
    {"2", "#", "#", "#"},
    {"3", "#", "#", "#"}
};

for(int i = 0; i < spielfeld.GetLength(0); i++)
{
	for(int j = 0; j < spielfeld.GetLength(1); j++)
	{
		Console.Write(spielfeld[i,j]);
	}
	Console.WriteLine();
}
```

