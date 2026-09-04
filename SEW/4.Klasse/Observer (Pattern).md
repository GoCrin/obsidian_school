Jedes Objekt hat einen Zustand, in dem es sich aktuell befindet. Bei Änderungen an diesem Zustand kann es vorkommen, dass es andere Objekte gibt, die von diesem einen Objekt abhängig sind und von solchen Zustandsänderungen benachrichtigt werden möchten. Man bezeichnet diese abhängigen Objekte als Observer und das zu beobachtende Objekt als Subjekt.

Das gewünschte Verhalten des Observer Pattern kann man folgendermaßen erreichen:
* Man kann Observer bei einem Subjekt "anmelden".
* Jeder Observer hat eine update-Methode, in der der eigene Zustand aktualisiert wird.
* Ändert sich der Zustand eines Subjekts werden die Observer benachrichtigt (english: to notify) indem deren update-Methode aufgerufen wird

![[Pasted image 20260506121720.png|499]]
![[Pasted image 20260513101424.png]]