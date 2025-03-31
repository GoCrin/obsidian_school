
Arbeitet von OSI Layer 2-7

![[Pasted image 20250331081154.png]]
![[Pasted image 20250331082228.png]]

# Software Firewall (aka. personal Firewall)

Rennt auf Endgerät

Arbeitet typischer weiße auf OSI-Layer 5 aufwärts

# Hardware Firewall

Auch bekannt als: externe Firewall, vorgelagerte Firewall, dedizierte Firewall

Arbeitet typischer weiße auf OSI-Layer 3 und 4

## Was schaut die Firewall an?

Meist wird nur der Header analysiert, da Daten meist verschlüsselt sind und sie so groß sind, dass es zu teuer (zeit intensiv) wäre um Daten sinnvoll zu analysieren.
### stateful inspection

Schaut jedes Paket ohne Kontext an
### stateless inspection

kann Kontext, wie z.B. Antworten auf von innen gesendete Pakete, erkennen.
### deep packet inspection (Nutzdaten analyse)

Analysiert nicht nur Header sondern auch Daten des Pakets.

# Transparenz

Ist die Firewall transparent, sieht ein Prozess, dass die Firewall "im Weg" ist.
Sonst sieht der Prozess nichts


# Firewall-Regeln

Meist wird etwas blockiert durchgelassen oder weiter geleitet
Meist wird alles "gelogged" aber es kann auch Regel oder Port abhängig "gelogged" werden

Regeln werden meist untereinander Sortiert die erste Regel die blockieren würde blockiert. Darunter liegende Regeln werden meist nicht weitergeleitet.
	Dies ist Hardware schonender

Bei neuerer Hardware können auch alle Einträge durchlaufen werden 

## White- vs. Blacklist

### Whitelist

* lässt grundsätzlich nichts durch außer Listeneinträge

### Blacklist


Was schaut sich die an

stateful - inspection vs stateless inspection 

das der versteht was eine verbindung ist
