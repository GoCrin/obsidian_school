# Netzwerkdiagramm

![[Pasted image 20260916160935.png]]
von Felix Jagadits

# Konfiguration der Mikrotik-Switches


```router-os
/interface bridge
add name=br protocol-mode=none

/interface bridge port
add bridge=br interface=ether2
add bridge=br interface=ether3
add bridge=br interface=ether4
```

# Konfiguration der Laptops

Die Laptops als Clients bekommen statische IP-Adressen im `10.0.0.0/24` Netzwerk von `10.0.0.10` bis `10.0.0.13`.

# Traffic ohne Switching-Loop

![[Pasted image 20260916155500.png]]

Der Traffic setzt sich aus einzelnen ARP-Requests der Laptops & MAC-Telnet zusammen. 

# Traffic mit Loop

![[Pasted image 20260916155911.png]]

Man sieht, dass sich der Traffic knapp verzehnfacht, doch dieser Wert scheint über eine Minute stabil zu bleiben und nicht weiter zu steigen.

# Doppelter Switchen-Loop

![[Pasted image 20260916161840.png]]

Der Traffic an der Schnittstelle scheint sich nicht zu ändern.