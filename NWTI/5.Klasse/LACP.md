Link Aggregation Control Protocol, definiert in 802.3ad

Portchannel

Hash-policy:
- Layer 2
- Layer 3
- Layer 2 + 3
- (Ports \[Layer 4\])

Als 1. dieses bonding von min. 2 ports machen und dann zu einer bridge hinzufügen
```
// sender policy, wenn der switch was bekommt geht er so damit um und sendet es weiter



/interface/bonding/add mode=802.3ad transmit-hash-policy=layer-2-and-3 name=MeinBond
```

```
conf t
interface port-channel 10

int gi0/0
channel-group 10 mode active

int gi0/1
channel-group 10 mode active
```

zum Testen 2 clients pro Seite (weil ein client immer dasselbe Kabel verwendet) mit iperf3

```bash
# 1. Gerät
# -s für Server
iperf3 -s


# 2. Gerät
# -c für Client
iperf3 -p 5001 -c 10.0.0.1
```