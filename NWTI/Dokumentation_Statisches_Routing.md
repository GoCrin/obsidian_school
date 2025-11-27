# Team
* Marcel Dietz
* Felix Jagadits
* Katja Riedl
* Linus Lichtenwallner
# Plan

Es wurde Folgender Plan für die Übung aufgebaut.

![[Pasted image 20251023121928.png]]

# Traceroute mit allen Verbindungen

## Von 192.168.20.10 zu 172.16.10.10

![[Pasted image 20251127111438.png]]

## Von 192.168.10.10 zu 192.168.0.10

![[Pasted image 20251127115238.png]]
# Traceroute mit einer getrennten Verbindung

Vor der Durchführung der nächsten `traceroute` Befehle wird die Verbindung zwischen Router 3 und Router 2 getrennt

## Von 192.168.20.10 zu 172.16.10.10

Der gewählte Weg ändert sich, da der (nach Hop-count sortierte) kürzeste Weg nicht mehr verfügbar ist.

![[Pasted image 20251127114836.png]]

## Von 192.168.10.10 zu 192.168.0.10

Der Weg bleibt exakt gleich.

![[Pasted image 20251127115356.png]]