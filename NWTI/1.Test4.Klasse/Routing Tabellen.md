# Aufbau
* Dest-Network
	* Meist Subnetze
	* 0.0.0.0/0 -> Default Route auf vielen Endgeräten
* Next hop / Gateway (oder Device / Interface, wenn direkt verbunden) 
	* Wem gibt man das IP-Paket
	* ether2
* Metrik
	* Kosten / Bewertung für Routen
* Src IP
# auf Rechner Anzeigen
## Linux
```Bash
ip route
```
## Windows
```PowerShell
route print
```

# Wählen eines Routingeintrags

Gewählt wird durch einen "longest prefix match", welcher den spezifischsten Eintrag (den mit den meisten Net-bit aka. höchste Subnetzmaske `/24`)

## Wählen einer Route, bei redundanten Einträgen

Mikrotik wählt eine Route (zufällig) aus und verwendet diese bis sie ausfällt.
In Cisco lässt sich durch die Metrik einer Route steuern wie gut diese ist (Weg mit der kleinsten Metrik wird gewählt). In Mikrotik heißt diese Zahl "Distance".

# Arten der Routingprotokolle
Man kann diese Protokolle wie folgt unterscheiden
* linkstate und distance vektor
* interior gateway protocol und extrior gateway protocol

# Übung

| Zielnetz      | Subnetmask      | Next-Hop      | Schnittstelle | Metrik |
| ------------- | --------------- | ------------- | ------------- | ------ |
| 192.168.0.0   | 255.255.248.0   | 192.168.0.1   | eth0          | 10     |
| 192.168.4.0   | 255.255.252.0   | 192.168.4.254 | eth1          | 5      |
| 182.168.4.128 | 255.255.255.128 | 192.168.4.129 | eth2          | 15     |
| 172.16.0.0    | 255.255.0.0     | 172.16.1.1    | eth3          | 20     |
| 0.0.0.0       | 0.0.0.0         | 192.168.0.254 | eth0          | 100    |

Geben sind 2 Adressen, diese sind durch die Routing Tabelle einem Anschluss / next Hop zu zu ordnen.

| Ziel Adresse  | Gewählter Routing Eintrag |
| ------------- | ------------------------- |
| 192.168.3.15  | 1.                        |
| 192.168.4.200 | 3.                        |
| 172.16.255.15 | 4.                        |
| 10.0.0.5      | 5.                        |
| 192.168.8.1   | 5.                        |
