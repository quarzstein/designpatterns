## Singleton-Pattern

### Das Singleton gewährleistet, dass ein Objekt nur einmal im Speicher vorhanden ist.

####
Der Zugriffsmodifikator "private" für den Standard-Konstruktor verhindert die Erzeugung von Objekte durch diesen.
Statt dessen erfolgt die Instanzierung durch eine Klassenmethode, welche das Objekt in einer statischen Klassenvariablen speichert. 
Dies geschieht beim erstmaligen Aufruf der Methode. Bei weiteren Aufrufen wird lediglich das Objekt als Variable zurückgegeben.

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
