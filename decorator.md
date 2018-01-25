# Decorator Pattern

## Beschreibung

Beim Decorator Pattern kann beliebige Funktionalität zu Objekten hinzugefügt
werden. Es gibt Basisklassen (Components/Komponenten). Diese werden mit
Decorators/Dekorierer erweitert. Decorator und Component sind vom gleichen Typ
(abstrakte Basisklasse oder Interface). Dekorator ruft immer die unterliegende
Implementierung einer Methode auf, und davor oder danach seine eigene.
Dekorators können beliebig verschachtelt werden.

## Vorteile

* Manipulation von Klassen kann zur Laufzeit und während dem Kompilieren
erfolgen
* Beliebige (Mehrfach)Kombination von Decorators ist möglich
* Das Interfaces, welches Clients nutzen, bleibt unverändert
* Klassen sind sehr kurz und übersichtlich, Sie implementieren nur das nötigste

## Nachteile

* Ggf sehr viele Klassen, dies kann unübersichtlich werden

## Beispiel

```csharp
    public abstract class Component
    {
        public abstract void operate();
    }

    public class ConcreteComponent1 : Component
    {
        override public void operate()
        {
            Console.WriteLine("this is a concrete component");
        }
    }

    public class ConcreteComponent2 : Component
    {
        public override void operate()
        {
            Console.WriteLine("This is another concrete component");
        }
    }

    public class ConcreteDecorator1 : Decorator
    {
        public ConcreteDecorator1(Component component) : base(component)
        {

        }
        override public void operate()
        {
            component.operate();
            Console.WriteLine("This is a concrete decorator number one");
        }
    }


    public abstract class Decorator : Component
    {
        protected Component component;

        public Decorator(Component component)
        {
            this.component = component;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Component CompA = new ConcreteComponent1();
            CompA.operate();
            CompA = new ConcreteDecorator1(CompA);
            CompA.operate();
            Console.ReadLine();
        }
    }
```
