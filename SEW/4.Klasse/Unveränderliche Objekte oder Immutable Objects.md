Der innere Zustand eines unveränderlichen Objekts bleibt immer konstant, nachdem es erzeugt wurde. Damit ist sichergestellt, dass sich unveränderliche Objekte über die gesamte Lebenszeit gleich verhalten. Wie kann Unveränderlichkeit erreicht werden?

* Keine "setter"-Methoden in der API der Klasse zur Verfügung stellen
* Alle Eigenschaften "final" und "private" setzen
* Aberben verbieten (Keine Subklassen) Die Klasse als "final" deklarieren (`public final class User`)

Im JDK sind Beispiele für unveränderliche Klassen: String, Wrapper Klassen wie Integer und Long.

## Vorteile

* Einfach zu verwenden und zu testen
* Automatisch "Thread-Sicher" und keine Synchronisationsprobleme, da der innere Zustand nicht verändert werden kann, sehen alle Threads immer das Gleiche
* Default "clone"-Methode funktioniert, keine eigene Implementierung notwendig

Speziell in Multithread-Umgebungen bieten unveränderliche Objekte den entscheidenden Vorteil der Thread-Sicherheit. Webservices beispielsweise sollten immer Thread sicher realisiert sein, da viele Clients darauf zugreifen können.