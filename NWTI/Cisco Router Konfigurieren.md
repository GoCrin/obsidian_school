## Liste der Befehle

| Befehl  | Beschreibung                          |
| ------- | ------------------------------------- |
| enable  |                                       |
| exit    | geht eine Ebene nach oben.            |
| end     | wechselt vom conf mode zum privileged |
| disable | geht aus dem enable mode.             |

## Typische Abläufe

### statisches Routing

```
enable
configure terminal
interface fa0/1
ip address 10.0.0.2 255.255.255.252
exit
ip route <ziel net> <mask> <next hop> <Metrik>
no shut
router rip
version 2
network <zu verteilendes Netz> <Subnetmask>
show ip route (Routingtabelle anzeigen)
write
copy running-cofig startup-config
```

### Verwendung von RIP
```
enable
configure terminal
router rip
version 2
network <Netz welches am Router angeschlossen ist(z.B.:192.168.0.0)>
```

### Verwendung von OSPF
```
enable
configure terminal
router ospf <Prozess-ID>
network <Netz welches am Router angeschlossen ist> <Wildcard-Mask> area <N>
```
Kosten können auf Interfaces gesetzt werden
```
enable
configure terminal
int <interfaces>
ip ospf cost <Kosten-Zahl>
```

OPSF Routing-Einträge anzeigen
```
sh ip route ospf
```

# VLAN konfigurieren
```
enable
configure terminal
vtp mode server
vtp domain 4bhits
vtp version 3
vtp password letmein
hostname CiscoSwitch
vlan 10
do show vlan brief
name Mitarbeiter
vlan 20
exit
interface Gi0/0
switchport trunk encapsulation dot1q
switchport mode trunk
interface Gi0/1
switchport mode access
switchport access vlan 10
```

Weißt dem Interface in einem Schritt die VLAN-ID 10 zu.
```
interface fa0/1.10
```
## VLAN Trunking Protocol

# MERKTS euch config_backup
