## DHCP-Server
Sollte auf selben Rechner wie domain-controller laufen. Wenn es keinen domain-controller gibt (wie z.B. bei Heimnetz) läuft der DHCP-Server meist auf Router.
Liefert:
* IP-Adressen-Reservierung
* Subnetzmaske
* Gateway
* 2xDNS-Server (IP)

Kommt zum Einsatz, wenn Client noch nie zuvor im Netz des Servers war (oder lease-time abgelaufen ist)


## DHCP-Client
Läuft auf Endgerät (PC, Laptop, Drucker)

NIC (Network Interface Controller)

## Ablauf
1. Client (Weiß noch gar nichts): Schickt Broadcast und hat selbst IP-Adr. 0.0.0.0
2.  3 Fälle
	1. Es gibt keinen DHCP-Server: Client bekommt keine IP oder Windows Standard IP
	2. Es gibt einen DHCP-Server: Server schickt Client oben genannte Daten (IP, etc.)
	3. Es gibt mehr als einen DHCP-Server: