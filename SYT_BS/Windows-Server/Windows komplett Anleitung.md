# Fragen
1. Welche optionen muss man übergen
	A: dns standard-gateway
2. 

statische ip

Netzwerkverbindungen
Doppel click
Eigenschaften
Internetprotokoll v4


## Server manager
### DNS & DHCP installieren

* Verwalten -> Features hinzufügen
* Serverrollen auswählen
* DNS
* DHCP
* weiter weiter ...
* zur Sicherheit nach Download neu starten

### DHCP
Tools -> DHCP
Aufklappen
IPv4
RMB- Neuer Bereich
name: DHCP_3bhits
start: 10.0.10.100
end: 10.0.10.200
Lease: 8 Tage
Router: 10.0.1.1

Bereichsoptionen 
* Wichtig sind: DNS-Server und Router
* Möglich:

in Leases RMB auf Webserver -> Reservierung hinzufürgen
### DNS

Tools -> DNS
DNS-Server konfigurieren
Schritte wie in [[Windows DNS]]




### Webserver mit mehreren dns einträgen
/etc/apache2/sites-available/000

```
<VirualHost *:80>
ServerName www.3bhits.local
...
```

Dafür braucht man eine 2. Forward lookup zone mit dem namen: www2
/etc/apache2/sites-available/001

```
<VirualHost *:80>
ServerName www2.3bhits.local
...
```