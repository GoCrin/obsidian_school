# Mikrotik

Konfiguration des Mikrotik-Switches, von Lichtenwallner.

```routeros
# 2026-05-21 08:55:40 by RouterOS 7.16  
# software id =    
#  
/interface bridge  
add name=br vlan-filtering=yes  
/port  
set 0 name=serial0  
/interface bridge port  
add bridge=br interface=ether1 pvid=20  
add bridge=br interface=ether2 pvid=10  
add bridge=br interface=ether3  
/interface bridge vlan  
add bridge=br tagged=ether3 untagged=ether1 vlan-ids=20  
add bridge=br tagged=ether3 untagged=ether2 vlan-ids=10  
/system note  
set show-at-login=no
```

## Funktionsnachweis

![[Pasted image 20260521110119.png]]

# Cisco

Konfiguration des Cisco-Switches, von Jagadits.

```
enable
configure terminal

vlan 10
name VLAN10

vlan 20
name VLAN20

interface gigabitEthernet0/0
switchport mode access
switchport access vlan 10
no shutdown

interface gigabitEthernet0/1
switchport mode access
switchport access vlan 20
no shutdown

interface gigabitEthernet0/2
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown

end
write memory
```

## Funktionsnachweis

![[Pasted image 20260521110310.png]]