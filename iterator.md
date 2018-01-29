# Iterator-Pattern

## Definition

Das Iterator-Pattern wird verwendet, um über eine Liste zu traversieren ohne hier entsprechend die Struktur oder das Muster zu
veröffentlichen. Heißt, eine Liste nach und nach Abzugehen. Der Iterator ist in diesem Fall der `Cursor`, welche durch die Kollektion
durchgeht.

## UML

![alt text](iterator_uml.png)

## Anwendung

Um einen Iterator Anwenden zu können, muss zuvor ein Iterator Interface angelegt werden, wo die entsprechenden Methoden (next, 
first,isDone und CurrentItem) erzeugt werden. Anschließend wird ein ConcreteIterator als Klasse definiert, damit der Iterator weiß, an 
welcher Stelle dieser sich gerade befindet.

Beispielcode für die Erstellung und Erzeugung eines Iterator-Pattern:

### Erzeugen des Iterator Interfaces

```csharp
interface IIterator
{
    string FirstItem { get;}
    string NextItem{ get;}
    string CurrentItem{ get;}
    bool IsDone { get;}
}
```

### Erzeugen des Interfaces für die Aggregator Kollektion

```csharp
interface IAggregate
{
    IIterator GetIterator();
    string this[int itemIndex]{set;get;}
    int Count{get;}
}
```

#### Erzeugen der Konkreten Klasse für die Aggreator Kollektion

```csharp
class MyAggregate : IAggregate
{
    List<string> values = null;

    public MyAggregate()
    {
        values = new List<string>();
    }

    #region IAggregate Members

    public IIterator GetIterator()
    {
        return new MyIterator(this);
    }

    #endregion

    public string this[int itemIndex]
    {
        get
        {
            if (itemIndex < values_.Count)
            {
                return values[itemIndex];
            }
            else
            {
                return string.Empty;
            }
        }
        set
        {                
            values.Add(value);                                
        }
    }

    public int Count
    {
        get
        {
            return values.Count;
        }
    }
}
```

#### Implementieren des Konrekten Interator

```csharp
class MyIterator : IIterator
{
    IAggregate aggregate = null;
    int currentIndex = 0;

    public MyIterator(IAggregate aggregate)
    {
        aggregate = aggregate;
    }

    #region IIterator Members

    public string FirstItem
    {
        get
        {
            currentIndex = 0;
            return aggregate[currentIndex];
        }
    }

    public string NextItem
    {
        get
        {
            currentIndex += 1;

            if (IsDone == false)
            {
                return aggregate[currentIndex];
            }
            else
            {
                return string.Empty;
            }
        }
    }

    public string CurrentItem
    {
        get
        {
            return aggregate[currentIndex];
        }
    }

    public bool IsDone
    {
        get
        {
            if (currentIndex < aggregate.Count)
            {
                return false;
            }
            return true;
        }
    }

    #endregion
}
```

#### Einfügen in das eigentliche Programm

```csharp
class Program
{
    static void Main(string[] args)
    {
        MyAggregate aggr = new MyAggregate();

        aggr[0] = "1";
        aggr[1] = "2";
        aggr[2] = "3";
        aggr[3] = "4";
        aggr[4] = "5";
        aggr[5] = "6";
        aggr[6] = "7";
        aggr[7] = "8";
        aggr[8] = "9";
        aggr[9] = "10";

        IIterator iter = aggr.GetIterator();

        for (string s = iter.FirstItem; iter.IsDone == false;  s = iter.NextItem )
        {
            Console.WriteLine(s);
        }
    }
}
```

Quelle: [Codeproject](https://www.codeproject.com/Articles/362986/Understanding-and-Implementing-the-Iterator-Patter)
