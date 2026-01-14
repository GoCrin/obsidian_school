# zeigen von Config

Anzeigen von verwendeten Befehlen
```
/ip/route/export
```

Zeigen der Routing Tabelle
```
/ip/route/print
```

Gibt alle durch OSPF bekommen Routen aus

```
/routing/route/print detail
```

Zeigt alle OSPF-Nachbarn
```
/routing/ospf/neighbor/print
```

```
/routing/ospf/instance/print
/routing/ospf/area/print
/routing/ospf/interface-template/print
```

# statisches Routing

IPv4 Adresse an Interface
```
/ip/address/add address=10.0.0.1/24 interface=ether1
```

statische Route erstellen
```
/ip/route/add dst-address=10.0.10.1/24 gateway=192.168.0.1 distance=1
```

# Ospf

Ospf magie von Mikrotik wirken lassen.
```
/routing/ospf/instance
add name=ospf_instance redistribute=connected, ospf router-id=1.1.1.1

/routing/ospf/area
add name=backbone instance=ospf_instance

/routing/ospf/interface-template
add area=backbone interfaces=ether1, ether2 cost 10
```

`router-id`: muss in einem Ospf-Netzwerk einzigartig sein.
