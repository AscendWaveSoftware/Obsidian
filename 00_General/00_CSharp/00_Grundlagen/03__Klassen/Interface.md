---
aliases:
  - Schnittstellen
tags:
  - interface
  - csharp
  - grundlagen
  - klassen
  - oop
---

>[!Info]- Eine andere Möglichkeit, in C# Abstraktion zu erreichen, sind **Interfaces**.


Ein interface ist eine vollständig "**abstrakte Klasse**", die nur abstrakte Methoden und Eigenschaften (mit leerem Hauptteil) enthalten kann.

```csharp
// interface
interface Animal
{
	void animalSound(); //interface methode ohne hauptteil
	void run(); //interface methode ohne hauptteil
}
```


>[!Info]- Bei der Namensgebung gilt als gute Praxis, am Anfang einer Schnittstelle mit dem Buchstaben "I" zu beginnen, da sich so besser gemerkt werden kann, dass es sich um eine Schnittstelle und nicht um eine Klasse handelt.

>[!Note]- Hinweis
>Schnittstellen können Eigenschaften und Methoden enthalten, aber keine Felder.


Um auf die Methoden eines Interfaces zugreifen zu können, muss das Interface von einer anderen Klasse "implementiert" werden (so ähnlich wie beim Vererben). Um ein Interface zu implementieren, verwendet man das "**:**"-Symbol (genau wie bei der Vererbung). Der Methodenkörper der Interface-Methode wird von der Klasse bereitgestellt, die das Interface implementiert. Beim Implementieren eines Interfaces muss nicht das Schlüsselwort **override** verwendet werden.

```csharp
// Interface
interface IAnimal
{
	void animalSound(); // interface methode ohne hauptteil
}

// Pig implementiert das IAnimal Interface
class Pig : IAnimal
{
	public void animalSound()
	{
		// Hauptteil von animalSound() wird hier bereitgestellt
		Console.WriteLine("Pee Pee");
	}
}

class Program 
{
	static void Main(string[] args)
	{
		Pig myPig = new Pig(); // Pig-Objekt wird erstellt
		myPig.animalSound();
	}
}
```


**Hinweise zu Interface**:

- Genau wie abstrakte Klassen können Interfaces **nicht verwendet werden, um Objekte zu erstellen** (im obigen Beispiel ist es nicht möglich, ein "IAnimal"-Objekt in der **Program-Klasse** zu erstellen.)
- Methoden in Interfaces **haben keinen Methodenkörper** - der Methodenkörper wird von der Klasse bereitgestellt, die das Interface implementiert.
- Bei der **Implementierung eines Interfaces müssen alle Methoden des Interfaces überschrieben (implementiert)** werden.
- Interfaces können **Eigenschaften (Properties)** und **Methoden**, aber **keine Felder oder Variablen** enthalten.
- Alle Mitglieder eines Interfaces sind standardmäßig **abstrakt** und **public**.
- Ein Interface kann **keinen Konstruktor enthalten**, da man von einem Interface **keine Objekte erstellen** kann.


**Warum und wann sollte man Interfaces verwenden?**

1. **Zur Erhöhung der Sicherheit** - bestimmte Details eines Objekts verstecken und nur die wichtigen Informationen über das Objekt (durch das Interface) sichtbar machen.
2. **Mehrfachvererbung ermöglichen** - C# unterstützt keine Mehrfachvererbung (eine Klasse kann nur von einer einzigen Basisklasse erben.)
   -> **Interfaces bieten eine Lösung**, da eine Klasse **mehrere Interfaces gleichzeitig implementieren** kann. 
   **Hinweis** : Um mehrere Interfaces zu implementieren, trennt man sie mit einem **Komma**.