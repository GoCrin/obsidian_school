# Virtuelle LANs

Auftrennung einer großen Broadcast-Domäne in kleinere Segmente / Broadcast-Domänen

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



![[Pasted image 20250307102318 1.png]]
Im Fall dieser Abbildung (Kreise = Endgeräte) gibt kein Standard für VLANs vor, eine VLAN_ID mit zuschicken. Paket von linken Switch ist im VLAN 1 und schickt Paket an Gerät an Port im VLAN 2.
**IEEE 802.1Q** legt 

![[Ethernet_802.1Q_Insert 1.svg]]

Es gibt dynamische Methoden und es gibt Port basierte Methoden
Einfachste Methode VLANs zu implementieren ist die Port-basierte Methode

### Tagged vs Untagged
IP-Paket entweder mit oder ohne Tag. Tags werden benötigt, wenn z.B. 2 Swiches 2 VLANs haben (auf jedem Switch sind Ports von beiden VLANs). In dem Fall würde man ohen Tags jedes VLAN mit einem physischen Kabel verbinden müssen. Mit Tags braucht man nur noch eine Verbindung (namens VLAN Trunk). Meist können nur Switches mit diesen Tags(bytes im header) umgehen, weshalb die VLAN Tags in den Paketen bevor sie am Endgerät ankommen entfernt werden müssen.


