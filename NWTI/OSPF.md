* "Open Shortest Path First" ist ein sogenanntes Interior Gateway Protokoll. bei Internet Service Providern (ISP) für internes Routing.
* zählt zu den Link-State-Protokollen -> Routingentscheidungen auf Basis der Qualität (z.B. Übertragungsgeschwindigkeit / Bandbreite, Verfügbarkeit einer Verbindung) des Links bzw. der Verbindungen
* "Kosten" können manuell für jede Verbindung konfiguriert werden
* Routingentscheidungen basieren auf den geringsten Kosten

## Ablauf
* "Hello"-Pakete werden auf allen aktivierten Interfaces mit Multicast ins Netzwerk geschickt.
* Nachbarn antworten mit Unicast-Paketen
* LSA (Link State Advertisments) werden ausgetauscht und LSDB (Link State Daten Bank) wird aufgebaut
* Dijkstra-Algorithmus wandelt die Informationen in der LSDB in eine Routingtabelle um.
* Danach wird basierend auf dieser Tabelle (geringste Kosten die Routingentscheidung) getroffen