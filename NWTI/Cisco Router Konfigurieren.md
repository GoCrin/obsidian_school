## Liste der Befehle

| Befehl | Beschreibung |
| ------ | ------------ |
| enable |              |

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