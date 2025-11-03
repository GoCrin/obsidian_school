```Bash
ping 8.8.8.8
```
1. macht ein ICMP Paket
	* Header
		* Type = ECHO_REQUEST
		* Code = 0
	* ICMP Payload
2. IP-Header
	* Src-IP wird über Routingtabelle herausgefunden
3. Ethernet-Header

## Routingtabelle

Anzeigen lassen druch
```Bash
ip route
```
oder (für Windows)
```PowerShell
route print
```

* Dest-Network
	* Meist Subnetze
	* 0.0.0.0/0 -> Default Route auf vielen Endgeräten
* Next hop / Gateway (oder Device / Interface, wenn direkt verbunden) 
	* Wem gibt man das IP-Paket
	* ether2
* Metrik
	* Kosten / Bewertung für Routen
* Src IP

### Bsp

`192.168.10.0/24 dev LAN1 src 192.168.10.10`
Sind im selben Layer 2 Segment (Gateway wird nicht benötigt), arp kann direkt ausgeführt werden

### Aufgaben

**1. Aufgabe**

\<Diagramm von Fischer hier\>

Routingtabelle:

| Router                  | Dest. Network   | Next Hop / Interface |
| ----------------------- | --------------- | -------------------- |
| Router1                 | 192.168.0.0/24  | direct br            |
|                         | 10.0.0.0/30     | direct ether1        |
|                         | 10.0.0.4/30     | direct ether2        |
|                         | 172.16.10.0/24  | 10.0.0.6             |
|                         | 192.168.10.0/24 | 10.0.0.1             |
|                         | 192.168.20.0/24 | 10.0.0.1             |
|                         | 10.0.0.8/30     | 10.0.0.1             |
|                         | 192.168.30.0/30 | 10.0.0.1             |
|                         | 192.168.0.0/16  | 10.0.0.1             |
| Router2                 | 192.168.0.0/24  | 10.0.0.5             |
|                         | 192.168.10.0/24 | 10.0.0.9             |
|                         | 192.168.20.0/24 | 10.0.0.9             |
|                         | 172.16.10.0/24  | direct br            |
|                         | 10.0.0.0/30     | 10.0.0.9             |
|                         | 10.0.0.4/30     | 10.0.0.5             |
|                         | 10.0.0.8/30     | 10.0.0.9             |
|                         | 192.168.30.0/30 | 10.0.0.9             |
| Router3                 | 192.168.10.0/24 | direct br            |
|                         | 192.168.0.0/24  | 10.0.0.2             |
|                         | 192.168.20.0/24 | 192.168.30.1         |
|                         | 172.16.0.10/24  | 10.0.0.10            |
|                         | 10.0.0.0/30     | 10.0.0.2             |
|                         | 10.0.0.4/30     | 10.0.0.2             |
|                         | 10.0.0.8/30     | 10.0.0.10            |
|                         | 192.168.30.0/30 | 192.168.30.1         |
| Router4                 | 192.168.20.0/24 | direct br            |
|                         | 192.168.10.0/24 | 192.168.30.2         |
|                         | 192.168.0.0/24  | 192.168.30.2         |
|                         | 172.16.10.0/24  | 192.168.30.2         |
|                         | 10.0.0.4/30     | 192.168.30.2         |
|                         | 10.0.0.4/30     | 192.168.30.2         |
|                         | 10.0.0.4/30     | 192.168.30.2         |
|                         | 192.168.30.0/30 | 192.168.30.2         |
| Verkürzung der oberen 7 | 0.0.0.0/0       | 192.168.30.2         |

**2. Aufgabe**
```Bash
telnet 172.16.12.241
```

### Wählen eines Routingeintrags

Longest prefix match -> der spezifischste Eintrag (Meisten Net-bit)

### Ethernet Frame

Aus der Routingtabelle 

## Ablauf

### Ein Rechner an einen anderen Rechner

* ICMP Paket (Request)
	* Src: 192.168.10.1
	* Dest: 8.8.8.8
	* Protocol: 1 (ICMP)
* Wird an Router (91.114.39.20) (Gateway) geschickt
* Router sieht Private Src IP -> Macht NAT
* ICMP Paket (Request)
	* Src: 91.114.39.20
	* Dest: 8.8.8.8
	* Protocol: 1 (ICMP)
* 8.8.8.8 bekommt ICMP Paket -> Schickt Reply
* ICMP Paket (Reply)
	* Src: 8.8.8.8
	* Dest: 91.114.39.20
	* Protocol: 1 (ICMP)
* Router bekommt das Paket -> wandelt Dest wieder auf private IP um
*  ICMP Paket (Reply)
	* Src: 8.8.8.8
	* Dest: 192.168.10.1
	* Protocol: 1 (ICMP)
* Router leitet es an Rechner

### TCP

Ablauf ziemlich Gleich außer, dass im TCP header Src und Dst Port steht.
Diese werden verwendet um im Router eine Tabelle der mit NAT übersetzten IP zu erstellen, um diese wieder zurück übersetzen zu können

#### Tabelle im Router

(In diesen Tabellen wird auch das verwendete Protokoll gespeichert)

| Original IP   | Translated IP | Dst Port | Src Port |
| ------------- | ------------- | -------- | -------- |
| 192.168.10.10 | 91.114.39.20  | 443      | 41316    |
| 192.168.10.20 | 91.114.39.20  | 443      | 41316    |

Bei einer solchen Tabelle ist es möglich, dass Rechner die den selben Src. Port wählen es unmöglich machen, die Original IP herauszufinden.
Deshalb gibt es zusätzliche Spalten in der Tabelle

| Original IP   | Translated IP | Dst Port | Original Src Port | Translated Src Port |
| ------------- | ------------- | -------- | ----------------- | ------------------- |
| 192.168.10.10 | 91.114.39.20  | 443      | 41316             | 55689               |
| 192.168.10.20 | 91.114.39.20  | 443      | 41316             | 53244               |
Der Router macht jetzt nicht nur NAT sondern auch PAT2

# Wählen einer Route, bei redundanten Einträgen

Mikrotik wählt eine Route (zufällig) aus und verwendet diese bis sie ausfällt.
In Cisco lässt sich durch die Metrik einer Route steuern wie gut diese ist (Weg mit der kleinsten Metrik wird gewählt). In Mikrotik heißt diese Zahl "Distance".