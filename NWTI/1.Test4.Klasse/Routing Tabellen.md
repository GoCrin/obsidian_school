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
