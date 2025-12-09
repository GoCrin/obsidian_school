# OSPF

```routeros
/routing/ospf/instance
add name=ospf_instance redistribute=connected, ospf router-id=1.1.1.1
/routing/ospf/area
add name=backbone instance=ospf_instance
/routing/ospf/interface-template
add area=backbone interfaces=ether1, ether2 cost 10
```
`router-id`: unique im ospf-network

## Debugging
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
Für router 3
```routeros
/routing/ospf/instance
add name=ospf_instance redistribute=connected,ospf router-id=3.3.3.3
/routing/ospf/area
add name=backbone instance=ospf_instance
/routing/ospf/interface-template
add area=backbone interfaces=ether1,ether2,ether3 cost=5
```
Für router 4
```routeros
/routing/ospf/instance
add name=ospf_instance redistribute=connected,ospf router-id=4.4.4.4
/routing/ospf/area
add name=backbone instance=ospf_instance
/routing/ospf/interface-template
add area=backbone interfaces=ether1 cost=5
```