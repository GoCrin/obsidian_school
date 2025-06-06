# Theorie (NWTI)

DNS: Domain Name System

## Vorgänger / Konkurrenten

* (LM)Hosts: Handgeschriebene Dateien die wie dns Namen und IP's verbinden

# Praxis

13 root dns server (A-M)
Hunderte Instanzen dieser Server über selben IPs (13 für 13 Server) mit anycast erreichbar

Jeder DNS-Server besitzt Root Hints ()

### Top level domains

Verwaltet von root dns servern
* Länder (.at, .de)
* .com
* .org

Weil root dns server von "usa" verwaltet wird und diese top level domains vergeben, kritisieren manche Staaten diese, da sie keine top level domain bekommen. (nicht anerkannter Staat)

## Grober dns routing ablauf
Tool: nslookup

www.htl-hl.ac.at

Recursive lookup (Von root Server zu tatsächlichen namen)
1 Wer ist zuständig für .at -> mehrere Server
2 einen dieser .at server fragen wer für .htl-hl zuständig ab

| Record | Verwendung                                                                    |
| ------ | ----------------------------------------------------------------------------- |
| NS     | löst Namen auf                                                                |
| A      | löst IPv4 auf                                                                 |
| AAAA   | löst IPv6 auf                                                                 |
| CNAME  | löst Namen in anderen Namen auf                                               |
| MX     | mail exchanger                                                                |
| PTR    | Pointer Record                                                                |
| TXT    | Plain text für z.B. für Zertifikate um zu beweisen, dass man der Besitzer ist |

193.170.204.18
18.204.170.193.in-addr.arpa

DNS Server werden von niederen Dns Servern und Clients gecachet um last von ihnen zu nehmen. Root Dns server werden am längsten gecachet je weiter "unten" des du kürzer wird gecachet

Resolver: löst für clients resolve abfragen. (Schul dns server)
OpenResolver (z.B. google 8.8.8.8): Jeder darf zugreifen. Zu vermeiden wenn man selbst versucht Resolver zu machen. DNS verwendet utp (sehr leicht source ip zu ändern). DNS Server liefern bei kleinen anfragen große antworten. Nun kann wegen utp die dst ip geändert werden -> dos attacken werden leicht

Diese Attacke nennt sich DNS Amplification attack

Zonen Betreuer: liefern nur antworten für die


### Server auf Linux installieren


```
apt install bind9
```

aufgabe: welche files sind in /etc/bind dafür verantwortlich einen "gescheiten dns server" zu machen

```
cd /etc/bind
```

/etc/bind/named.conf.options
```
forwarders {
    8.8.8.8;
    8.8.4.4;
};
```

/etc/bind/named.conf.local
```
zone "3bhits.local" {
	type master;
	file "/etc/bind/zones/db.3bhits.local";
};
```
```
cp db.local db.3bhits.local
```
/etc/bind/db.3bhits.local
```
$TTL    604800
@       IN      SOA     3bhits.local. root.3bhits.local. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      3bhits.local.     ; 
@       IN      A       10.0.2.5             ; ip vom dhcp/dns server
```
```
mkdir zones
mv db.3bhits.local ./zones/db.3bhits.local
```
/etc/bind/zones/db.3bhits.local
```
$TTL    604800
@       IN      SOA     ns.3bhits.local. admin.3bhits.local. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.3bhits.local.
@       IN      A       10.0.2.5
ns      IN      A       10.0.2.5
www     IN      A       10.0.2.10
```
### Server auf Windows installieren

```
Install-WindowsFeature DNS -IncludeManagementTools
```

* tools -> DNS
* DNS-Server konfigurieren
* RMB -> neue Zone
	* weiter
	* primäre zone
	* forward lookupzone
	* zonenname: 3bhits.local
	* neue datei mit diesem namen erstellen
	* dynamische updates nicht zulassen
	* Soll dieser server weiterleiten? -> nein

* Foward-Lookupzonen -> 3bhits.local
	* RMB -> neuer host
	* www
	* ipaddr: irgendwas (z.B 10.0.2.12)
	* hosthinzufügen
	
www (geht auf) -> 10.0.2.12

im DHCP-Server muss nun der DNS-Server vergeben werden

```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```

