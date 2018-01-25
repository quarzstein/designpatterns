# Strategy Pattern

## Definition

Das Strategypattern ermöglicht es, den Algorithmus unabhängig von ihn nutzenden Klienten zu variieren.

## Aufbau

Das Verhalten eines Objekts wird in eine Klasse (Strategieklasse) ausgelagert. Für jedes Verhalten existiert eine Klasse.
Jede Klasse die das Verhalten nutzen soll kann eine Instanz der Strategieklasse nutzen.
Es wird nicht mit der konkreten Implementierung des Verhaltens, sondern mit einem Interface gearbeitet.

## Code

### Strategy-Interface + Konkrete Strategy

```csharp
interface Strategy()
{
  public void Algorithm();
}

class ConcreteStrategy1() : Strategy
{
  public void Algorithm()
  {
   //Code
  }
}

class ConcreteStrategy2() : Strategy
{
  public void Algorithm()
  {
   //Code
  }
}

class ConcreteStrategy3() : Strategy
{
  public void Algorithm()
  {
   //Code
  }
}
```

### Kontext

```csharp
abstract class Context
{
  //Instanzvariable. Standartverhalten.
  Strategy strategy = new ConcreteStrategy1();

  public void setStrategy (Strategy strategy)
  {
    this.strategy = strategy;
  }

  public void Behavior()
  {
    //Zuweisung des Verhaltens an Verhaltensobjekt
    strategy.Behavior();
  }
}
```

### Klient

```csharp
public class Client
{
  Context context = new Context();
  context.Behavior(); //Standartverhalten
  context.setStrategy(new ConcreteStrategy2);
  context.Behavior(); //ConcreteStrategy2 Verhalten
}
```
