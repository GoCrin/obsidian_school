**Routing Information Protocol**
Ist ein dynamisches Routing Protokoll welches UDP am Port 520 verwendet
* RIPv1:
	* Class-based-Protokoll
	* keine Authentifizierungsmöglichkeiten
	* keine Multicast Unterstützung
* RIPv2:
	* Class-less-Protokoll
	* Authentifizierungsmöglichkeiten
	* Multicast Unterstützung
* RIPng:
	* fügt IPv6 Unterstützung hinzu
---
* Es ist ein Distance-Vector-Protokoll. Heißt:
	* Distance ist bekannt (next hops, maximal 15 hops)
	* Vector ist bekannt (Richtung ist bekannt)

* (Es hat nie überblick über das gesamte Netzwerk)
* Dadurch, dass die Distance nur maximal 15 hops lang sein kann, ist das Protokoll auf sehr kleine Netze limitiert.
* Es verschickt alle 30 Sekunden die eigenen Netzwerkinformationen an benachbarte Router.
* Konvergenz: zustand in dem alle Router in einem Netzwerk die selben & aktuellen Netzwerkinformationen besitzen
* Konfiguration ist einfach
* Sehr langsam