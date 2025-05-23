## Warum?
IPv4 mit 32bit hat zu wenige IP's. Dieses Problem wurde mit öffentlichen und privaten IP-Adressen umgangen (NAT und PAT). Heutzutage wäre ein Umstieg auf IPv6 theoretisch möglich und wird teilweise gemacht, aber IPv6 ist noch lange nicht überall im Einsatz. Wurde Ende der 90er Jahre eingeführt

## Aufbau
* Länge: 128bit
* (übliche) Schreibweise: x:x:x:x:x:x:x:x (mit x = 2Byte = 16bit in hexadezimal) z.B.: 
* `fe80::d55f:5687:435a:d2cf`
* Man darf einmal pro Adresse einen oder mehr "Nullerblöcke" (`:0000:`) mit `::` ersetzen
* Führende Nuller werden weggelassen also: `f5` = `00f5`
* Die URI Darstellung von IPv6 ist in eckigen Klammern: `[<ip>]`
* ersten 8 byte: prefix, letzten 8 byte: interface identifier
* Man bekommt nicht eine IP-Adresse sondern einen ganzen Adressbereich ($2^{32}$ Adressen)

`194B:001C:0341:0000:0000:0FFF:0000:CB4F` -> `194B:1C:341::FFF:0:CB4F`
`4B::3A:0:FF` -> `004B:0000:0000:0000:0000:003A:0000:00FF`

`194B:001C:0341:0000:0000:0FFF:0000:CB4F:10.14.7.199`

**Killer Applikation** ist irgendwas was man will aber nur mit gewissen Eigenschaften (hier IPv6) nutzen kann. Diese fehlt bei IPv6 wodurch keiner umsteigt