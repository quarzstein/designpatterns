Observer-Pattern

Das Observer Pattern ermöglicht, dass sich Objekte (Observer, beobachtendes Objekt) 
bei einem anderen Objekt (Subjekt, beobachtetes Objekt) registrieren und fortan vom 
diesem informiert werden, sobald es sich ändert.

Die Idee hinter dem Pattern liegt darin, das sich Teile von einem Programm (meist grafische Elemente),
die identische Quellen benutzen, benachrichtigt werden, wenn sich etwas ändert.

Es werden dafür mindestens 3 Klassen benötigt.
zum Einem das Subjekt, bei dem sich der Konkrete Observer anmelden, abmelden, und benachrichtig wird.
Das Observer Interface stellt den Observern die "Update" Methode zur verfügung die von jedem Observer implementiert werden muss.
Und die Konkreten Observer können bei einer Benachrichtigung dann mit der Daten des Subjektes arbeiten. 