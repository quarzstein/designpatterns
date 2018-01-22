# Iterator Pattern

Iteratoren werden in der C# Entwicklung als Liste oder Arrays verwendet und beispielsweise als Interface `IEnumerable`
in dem Programmcode hinterlegt werden. Iteratoren, müssen nicht zwangsweise eine zusätzliche Klasse besitzen, sondern können
ebenfalls direkt aufgerufen werden, siehe unten im Beispiel. Sie geben hier entsprechend mit der `Yield Return`
Methode nacheinander die Werte zurück, welche definiert werden müssen.Ein Iterator wird in der Regel mit 
einer `foreach` Anweisung erzeugt. 

###Direkter Aufruf ohne IEnumerable Klasse
```
static void Main()  
{  
    foreach (int number in SomeNumbers())  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 3 5 8  
    Console.ReadKey();  
}  

public static System.Collections.IEnumerable SomeNumbers()  
{  
    yield return 3;  
    yield return 5;  
    yield return 8;  
}  

````

###Beispielcode /Hinterlegung einer IEnumerable Klasse mit Aufruf der Methode:
```
###Aufruf der Methode im Code
static void Main()  
{  
    DaysOfTheWeek days = new DaysOfTheWeek();  

    foreach (string day in days)  
    {  
        Console.Write(day + " ");  
    }  
    // Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey();  
}  


###Initialisierung der Klasse/Instanz
public class DaysOfTheWeek : IEnumerable  
{  
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };  

    public IEnumerator GetEnumerator()  
    {  
        for (int index = 0; index < days.Length; index++)  
        {  
            // Yield each day of the week. Aus 
            yield return days[index];  
        }  
    }  
}  
```
