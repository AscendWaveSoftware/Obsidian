---
aliases: 
tags:
  - abstraction
  - csharp
  - klassen
  - grundlagen
---
Unter **Datenabstraktion** versteht man den Prozess, bestimmte Details zu verbergen und dem Benutzer nur die wesentlichen Informationen zu zeigen.
Abstraktion kann entweder durch **abstrakte Klassen** oder durch **Schnittstellen (Interfaces)** erreicht werden. 

Das Schlüsselwort **abstract** wird für Klassen und Methoden verwendet:

- **Abstrakte Klasse**: Ist eine eingeschränkte Klasse, die nicht zur Erstellung von Objekten verwendet werden kann (um auf sie zuzugreifen, muss sie von einer andern Klasse **geerbt** werden).

- **Abstrakte Methode**: Kann nur in einer abstrakten Klasse verwendet werden und hat keinen Körper. Der Körper wird von der abgeleiteten Klasse bereitgestellt (geerbt von).



Eine abstrakte Klasse kann sowohl abstrakte als auch reguläre Methoden haben:

```csharp
abstact class Animal
{
	public abstract void animalSound(); // Abstrakte Methode ohne Körper

	public void sleep() // reguläre Methode
	{
		Console.WriteLine("Zzz");
	}
}
```


> [!Info]- Aus dem obigen Beispiel geht hervor, dass es nicht möglich ist, ein Objekt der Klasse Animal zu erstellen:
```csharp
Animal myAnimal = new Animal(); // Gibt einen Error aus (Cannot create an instance of the abstract class or interface 'Animal')
```


Um auf die abstrakte Klasse zugreifen zu können, muss sie von einer anderen Klasse **geerbt** werden. **Beispiel**:

```csharp
// Abstract Class
abstract class Animal 
{
	// Abstract Method (does not have a body)
	public abstract void animalSound();
	// Regular method
	public void Sleep () 
	{
		Console.WriteLine("Zzz");
	} 
}


// Derived class (inherit from Animal)
class Pig : Animal 
{
	public override void animalSound ()
	{
		// The body of animalSound() is provided here
		Console.WriteLine("The pig says: wee wee");
	}
}


internal class Program 
{
	static void Main (string[] args)
	{
		Pig myPig = new Pig(); // Create a Pig object
		myPig.animalSound(); // Call the abstract method
		myPig.sleep(); // Call the regular method
	}
}
```


>[!Note]- Warum und wann sollte man abstrakte Klassen und Methoden verwenden?
>Um **Sicherheit** zu erreichen - bestimmte Details zu verbergen und nur die wichtigsten Details eines Objekts anzuzeigen. **Hinweis**: Abstraktion kann auch mit Schnittstellen (Interfaces) erreicht werden.



