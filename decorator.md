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
