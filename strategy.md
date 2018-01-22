# Strategy Pattern

## Definition
Das Strategypattern ermöglicht es, den Algorithmus unabhängig von ihn nutzenden Klienten zu variieren.

## Aufbau
Das Verhalten eines Objekts wird in eine Klasse (Strategieklasse) ausgelagert. Für jedes Verhalten existiert eine Klasse.
Jede Klasse die das Verhalten nutzen soll kann eine Instanz der Strategieklasse nutzen.
Es wird nicht mit der konkreten Implementierung des Verhaltens, sondern mit einem Interface gearbeitet.

## Code

```csharp
interface Verhalten
{
  public void Verhalten();
}

class Verhalten1() : Verhalten
{
	// Deff. Verhalten1
}

class Verhalten2() : Verhalten
{
	// Deff. Verhalten2
}

class Verhalten3() : Verhalten
{
	// Deff. Verhalten3
}

abstract class Hauptklasse
{
	Verhalten verhalten = new Verhalten1();
}

public void setVerhalten (Verhalten verhalten)
{
	this.verhalten = verhalten;
}

public void Verhalten()
{
	verhalten.verhalten();
}

public class Client
{
	Hauptklasse hauptklasse = new Hauptklasse();
	hauptklasse.verhalten();
	hauptklasse.setVerhalten(new Verhalten2);
	hauptklasse.verhalten();
}
```
