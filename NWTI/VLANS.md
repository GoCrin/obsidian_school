# Virtuelle LANs

Auftrennung einer großen Broadcast-Domäne in kleinere Segmente / Broadcast-Domänen

Arbeiten auf **Layer 2**

Segmentierung basierend auf:
	Endgerätetypen (Notebooks, Drucker, IP-Telefonie, etc.)
	Abteilungen, Stockwerke
-> VLANs ermöglichen eine Priorisierung von Datenpaketen

### VLANs im Netzwerkprojekt
1. VLAN10: Notebootks/PC
2. VLAN20: Drucker
3. VLAN30: IP-Telefonie
4. VLAN40: Grafiker
5. VLAN50: Endgeräte auf Accesspoints (WLAN)

VLAN-Tag wird der Frame angehängt
	VLAN-IP
	Priorität



![[Pasted image 20250307102318.png|697]]
Im Fall dieser Abbildung (Kreise = Endgeräte) gibt kein Standard für VLANs vor, eine **VLAN_ID** (12bit) mit zuschicken. Paket von linken Switch ist im VLAN 1 und schickt Paket an Gerät an Port im VLAN 2.
**IEEE 802.1Q** (sollte man Wissen, da viele von einem IEE 802.1Q Header schreiben) fügt einen Header ein, diesen nennt man auch Tag

![[Ethernet_802.1Q_Insert.svg|697]]

Es gibt dynamische Methoden und es gibt Port basierte Methoden
Einfachste Methode VLANs zu implementieren ist die Port-basierte Methode

### Tagged vs Untagged

Tagged Ethernetframes haben VLAN-Informationen.
Untagged Ethernetframes haben dieses nicht.

IP-Paket entweder mit oder ohne Tag. Tags werden benötigt, wenn z.B. 2 Switches 2 VLANs haben (auf jedem Switch sind Ports von beiden VLANs). In dem Fall würde man ohne Tags jedes VLAN mit einem physischen Kabel verbinden müssen. Mit Tags braucht man nur noch eine Verbindung (namens VLAN Trunk). Meist können nur Switches mit diesen Tags(bytes im header) umgehen, weshalb die VLAN Tags in den Paketen bevor sie am Endgerät ankommen entfernt werden müssen.

Ein Endgerät (Laptop) kann (meist) nichts von dem VLAN wissen, in dem es ist, da es nur untagged Frames bekommt. 

### VLAN ID

Meist wird die VID 1 als default gesetzt um zu zeigen, dass man den Port nicht konfiguriert hat und sollte deshalb nicht verwendet werden.

# Arten die VID zu bestimmen

## Portbased

Administrator muss festlegen, an welchem Switch Port welche VID ist.
aggress liste → auf welchem port ein frame mit einer gewissen VID den switch wieder verlassen darf.
Es gibt 2 aggress listen, eine tagged- und eine untagged-liste, diese sind dazu da um festzulegen, wo der VLAN-Header mitgeschickt werden darf und wo nicht. 

In der tagged aggress liste wird der VLAN-Header mitgeschickt und in der untagged aggress liste wird der Header vor dem schicken entfernt. 

## Dynamische

In welches VLAN ein Frame kommt, ist nicht mehr von dem Port abhängig, sondern von anderen Parametern, wie welche Nutzer sich authentifiziert hat.