# Netzwerkdiagramm

![[Pasted image 20260923160807.png]]

Farbkodiert sind die Pafde wie sie links oben in der Skizze beschrieben wurden.

# Konfiguration

Die 5 Switches wurden konfiguriert, wobei jeder / jede Mitwirkender / Mitwirkende einen Switch konfiguriert hat, mit Ausnahme von einer Person welche 2 einrichtete.
Alle Konfigurationen sehen in etwa wie die des 5. Switches aus, welche hier gezeigt wird:
```routeros
/interface bridge
add name=br protocol-mode=mstp region-name=MST-Region region-revision=1 vlan-filtering=yes

/interface wifi configuration
add channel.frequency=5180 name=linusmikrotik ssid=LinusMikrotik

/interface wifi
set [ find default-name=wifi1 ] configuration=linusmikrotik disabled=no

/interface bridge msti
add bridge=br identifier=1 vlan-mapping=10
add bridge=br identifier=2 vlan-mapping=20
add bridge=br identifier=3 vlan-mapping=30

/interface bridge port
add bridge=br interface=ether3 pvid=10
add bridge=br interface=ether4 pvid=20
add bridge=br interface=wifi1 pvid=30
add bridge=br interface=ether1 path-cost=100
add bridge=br interface=ether2 path-cost=10

/interface bridge vlan
add bridge=br tagged=ether1,ether2 untagged=ether3 vlan-ids=10
add bridge=br tagged=ether1,ether2 untagged=ether4 vlan-ids=20
add bridge=br tagged=ether1,ether2 untagged=wifi1 vlan-ids=30
```

# durch MSTP generierte Konfigurationen

## Switch 1

![[Pasted image 20260923161432.png]]

## Switch 2

![[Pasted image 20260923161527.png]]
![[Pasted image 20260923161458.png]]

## Switch 3

![[Pasted image 20260923161547.png]]
![[Pasted image 20260923161558.png]]

## Switch 4

![[Pasted image 20260923161610.png]]
![[Pasted image 20260923161618.png]]

## Switch 5

![[Pasted image 20260923161632.png]]
![[Pasted image 20260923161640.png]]