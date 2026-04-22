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
# IPv6 Routing
```routeros
/ipv6 address
add address=fda2::1 interface=ether3
add address=fd00::2 advertise=no interface=ether1
add address=fd01::1 advertise=no interface=ether2
/ipv6 route
add dst-address=fda1::/64 gateway=fd01::2
add dst-address=fda0::/64 gateway=fd00::1

/ipv6/nd/set disabled=no numbers=0
```

# OSPFv3 (Für IPv6)
```routeros
/routing/ospf/instance
add name=ospf_instance redistribute=connected, ospf router-id=1.1.1.1 version=3
/routing/ospf/area
add area-id=0.0.0.0 name=backbone instance=ospf_instance
/routing/ospf/interface-template
add area=backbone interfaces=ether1, ether2 cost 10
```

```routeros
# Assign address on ether1 (link to upstream router)
/ipv6 address add address=fd50::1/64 interface=ether1 advertise=no

# Assign address on ether2 (client network)
/ipv6 address add address=fd16::1/64 interface=ether2 advertise=yes

/ipv6 nd set [find interface=ether2] advertise-dns=yes advertise-mac-address=yes hop-limit=64 interface=ether2 managed-address-configuration=no other-configuration=no ra-interval=20s-3m ra-lifetime=30m
    
/routing ospf instance add name=ospf-v3 version=3 router-id=6.9.69.21

/routing ospf area add name=backbone area-id=0.0.0.0 instance=ospf-v3

# ether1 - link to upstream router (point-to-point or broadcast)
/routing ospf interface-template add interfaces=ether1 area=backbone type=ptp

# ether2 - client network (broadcast, passive - no need to form adjacency with clients)
/routing ospf interface-template add interfaces=ether2 area=backbone type=broadcast passive=yes
```

# Wireguard

```
/interface/wireguard/add
/ip/address/add address=1.0.0.2
/interface/wireguard/peers/add allowed-address=192.168.20.0/24 endpoint-port=32903 interface=wg1 public-key="..."
```

```

```

wg1 interface braucht auch eine private ip Addresse z.B `192.168.30.1/30`