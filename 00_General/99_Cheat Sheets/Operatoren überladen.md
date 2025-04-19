---
aliases: 
tags:
  - operatoren
  - überladung
  - csharp
  - grundlagen
  - cheatsheet
---

**Operatoren (+,-,x,/)** haben unterschiedliche Funktionalitäten, je nachdem, welchen Typ die Operanden haben, auf die die Operatoren angewendet werden. Mit der **Operatorüberladung** können für eigene Typen (Klassen/Structs) eigene Funktionalitäten für Operatoren definiert werden.

```csharp
public class Bruch
{
    public int Zaehler { get; set; }
    public int Nenner { get; set; }

    public Bruch(int _zaehler, int _nenner)
    {
        Zaehler = _zaehler;
        Nenner = _nenner;
    }

    public static Bruch operator +(Bruch a)
    {
        return a;
    }

    public static Bruch operator -(Bruch a)
    {
        return new Bruch(-a.Zaehler, a.Nenner);
    }

    public static Bruch operator +(Bruch a, Bruch b)
    {
        return new Bruch(a.Zaehler * b.Nenner + b.Zaehler * a.Nenner, a.Nenner * b.Nenner);
    }

    public static Bruch operator -(Bruch a, Bruch b)
    {
        return a + (-b);
    }

    public static Bruch operator *(Bruch a, Bruch b)
    {
        return new Bruch(a.Zaehler * b.Zaehler, a.Nenner * b.Nenner);
    }

    public static Bruch operator /(Bruch a, Bruch b)
    {
        return new Bruch(a.Zaehler * b.Nenner, a.Nenner * b.Zaehler);
    }
}
```

Zuerst erhält die Klasse **Bruch** einen Konstruktor, der Werte für Zähler und Nenner entgegennimmt. Dann deklarieren wir für jeden Operator, den wir für den Typ Bruch überladen wollen, eine eigene Methode. Methoden, die Operatoren überladen, müssen **statisch** sein. Der Name einer Methode, die einen Operator überlädt, ist der Operator selbst. Vor den Namen der Methode schreiben wir das Schlüsselwort **operator**. Der **Rückgabetyp** einer Operatormethode ist der Typ, für den die Überladung gelten soll, in unserem Beispiel Bruch. Die Übergameparameter von Operatormethoden haben ebenfalls den Typ, für den die Überladung gelten soll - also auch Bruch. Ein Operator kann mehrere Überladungen für einen Typ haben.