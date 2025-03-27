---
aliases:
  - Zugriffsmodifikatoren
tags:
  - accessors
  - zugriffsmodifikatoren
  - csharp
  - grundlagen
  - cheatsheet
  - nestedclass
---
In **C#** steuern die **Schlüsselwörter** (Accessors) **public, internal** und **private** die Sichtbarkeit (Zugriffsmodifikatoren) einer Klasse.

## Public-Accessor

- Klassen, Methoden oder Eigenschaften, die mit **public** definiert sind, sind **uneingeschränkt zugänglich**.
- Sie können innerhalb des gleichen Projekts und auch von anderen Projekten oder Assemblies aus verwendet werden.

```csharp
public class MyClass
{
	public void Method()
	{
		
	}
}

// Zugriff ist von überall möglich
```


## Internal-Accessor

- Klassen, Methoden oder Eigenschaften, die als **internal** definiert werden, sind nur **innerhalb der gleichen Assembly** zugänglich.
- Ein Assembly ist typischerweise ein kompiliertes Projekt (.dll oder .exe-Datei).
- Damit kann verhindert werden, dass externe Projekte Zugriff auf dieses Klasse haben, aber weiterhin der Zugriff innerhalb des aktuellen Projekts erlaubt wird.

```csharp
internal class MyClass
{
	internal void Method() 
	{
	
	}
}

// Zugriff nur innerhalb desselben Projekts möglich
```



## Private-Accessor

- Klassen, Methoden und Eigenschaften, die mit **private** definiert werden, sind nur **innerhalb des umschließenden Bereiches** (z. B. innerhalb der gleichen Klasse oder Datei, im Fall von Klassen innerhalb einer anderen Klasse) zugänglich.
- Eine Klasse kann in C# nur dann mit dem Schlüsselwort **private** versehen werden, wenn sie **verschachtelt innerhalb einer anderen Klasse** definiert wird (**Nested class**).
- **Top-Level-Klassen** (**direkt in Namespace-Ebene**) dürfen NICHT mit private markiert werden.

```csharp
public class OuterClass
{
	private class InnerClass
	{
		public void Method()
		{
			
		}
	}

	public void TestMethod
	{
		InnerClass inner = new InnerClass();
		inner.Method();
	}
}

// InnerClass ist außerhalb von OuterClass NICHT erreichbar
```



| Zugriffsmodifizierer | Innerhalb der Klasse | Innerhalb des Projekts (Assembly) | Externe Projekte |
| -------------------- | -------------------- | --------------------------------- | ---------------- |
| **public**           | Ja                   | Ja                                | Ja               |
| **internal**         | Ja                   | Ja                                | Nein             |
| **private**          | Ja                   | Nein                              | Nein             |
