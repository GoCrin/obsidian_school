Spanning Tree Protocol (STP)

Was ist der Zentrale Punkt im Netzwerk (Route-Bridge)? Es setzt diesen Punkt zufällig. Priority (vom admin) und mac des switches werden zusammen "gerechnet" (prio concat. mac), und die mit dem niedrigsten Wert wird zur Route-Bridge.

STP ist standardmäßig aktiv, weshalb man auf jedem switch die gewünschte Priority setzten sollte.

Die Route-Bridge ist nur relevant, wenn das Netz nicht schleifenfrei ist.

Bei STP kann für jedes Interface Kosten definiert werden. Wichtig, wenn man standardmäßig die schnellste Verbindung aktiv haben will.

Jeder Switch schickt eine BPDU mit seiner Bridge-ID und der kleinsten Bridge-ID die der Switch jemals bekommen hat.

Wenn Route-Bridge bekannt ist, sendet diese BPDU's mit Kosten 0 an alle Nachbarn weiter. Diese Nachbarn addieren die Kosten der Schnittstelle, auf der sie das BPDU erhalten haben und senden diese weiter. Nach einer Zeit nimmt der Switch die niedrigsten Kosten und macht sie zur **route-path-cost**.

---

Route-Bridge election

Günstigste Wege zur Route-Bridge werden berechnet.

In einem Netz aus Switches schickt jeder eine BPDU mit seiner Bridge-ID under der **kleinsten Bridge-ID** die dieser Switch jemals bekommen hat. Dadurch findet man die **Route-Bridge** (Switch mit kleinster Bridge-ID). Jetzt wird ein **Spanning Tree** unter Berücksichtigung von **Kantengewichten** ausgehend von der Route-Bridge gebaut.

# Bridge-ID

Switch mit kleinster Bridge-ID wird zur Route-Bridge.

2 Byte: bridge priority (muss $n \cdot 4096$ sein)
6 Byte: Mac-Addresse

![[Pasted image 20260914100151.png]]

# BPDU

Bridge Protocol Data Unit

# Switching loops

Wenn zwischen Switches ein "Ring" ist, sorgen diese dafür, dass Frames unendlich lange im Kreis geschickt werden. Bei besonders ungünstigen Verkabelungen wächst die Anzahl an Frames exponenziell und verbraucht somit nach kurzer Zeit die gesamte Bandbreite. Dieses Phänomen nennt man **Broadcaststorm**. 

# Interface Rollen

| Name            | Beschreibung                                                                                   | Farbe in Skizze |
| --------------- | ---------------------------------------------------------------------------------------------- | --------------- |
| Route Port      | Zeigen zur Routebridge                                                                         | grün            |
| Designated Port | ein Port der von der Routebridge weg zeigt.                                                    | hellblau        |
| Alternate Port  | zeigt auch zur routebridge wurde aber deaktiviert, weil es kleinere costs zur routebridge gibt | rot             |
| Backup Port     | zeigt von der routebridge weg und wurde deaktiviert                                            |                 |


# Konfiguration in Mikrotik

```router-os
/interface/bridge/add name=br priority=0x1000

/interface/bridge/port
add bridge=br interface=ether1 path-cost=10

/interface/bridge/monitor // viele zeigen weg, id von bridge
```