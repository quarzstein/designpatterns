## Singleton-Pattern

### 
Das Singleton gewährleistet, dass ein Objekt nur einmal im Speicher vorhanden ist.
Die Deklaration des Konstruktors als private verhindert, dass Objekte instanziert werden 
können. Statt dessen werden sie durch eine Klassenmethode erzeugt und in einer statischen 
Klassenvariablen gespeichert. Dies tut sie aber nur beim ersten einmal. Bei weiteren
Aufrufen wird lediglich das Objekt als Variable zurückgegeben.

### Status Klassen

####
```csharp

    public class TSingleton
    {
        private TSingleton() { }

        private TSingleton instance;

        public TSingleton Get_Instance()
        {
            if (instance == null) { instance = new TSingleton(); }
            return instance;
        }
    }
```
