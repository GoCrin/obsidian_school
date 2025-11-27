# Team
* Marcel Dietz
* Felix Jagadits
* Katja Riedl
* Linus Lichtenwallner
# Traceroute mit allen Verbindungen

## Von 192.168.20.10 zu 172.16.10.10

```
# traceroute 172.16.10.10
traceroute to 172.16.10.10 (172.16.10.10), 30 hops max, 60 byte packets
 1  _gateway (192.168.20.1)  0.177 ms  0.153 ms  0.140 ms
 2  192.168.30.2 (192.168.30.2)  0.207 ms  0.221 ms  0.209 ms
 3  10.0.0.10 (10.0.0.10)  0.334 ms  0.322 ms  0.310 ms
 4  172.16.10.10 (172.16.10.10)  0.504 ms  0.534 ms  0.521 ms
```
## Von 192.168.10.10 zu 192.168.0.10

```
# traceroute 192.168.0.10
traceroute to 192.168.0.10 (192.168.0.10), 30 hops max, 60 byte packets
 1  _gateway (192.168.10.1)  0.174 ms  0.148 ms  0.137 ms
 2  10.0.0.2 (10.0.0.2)  0.237 ms  0.312 ms  0.243 ms
 3  * 192.168.0.10 (192.168.0.10)  1.205 ms  1.194 ms
```
# Traceroute mit einer getrennten Verbindung

Vor der Durchführung der nächsten `traceroute` Befehle wird die Verbindung zwischen Router 3 und Router 2 getrennt

## Von 192.168.20.10 zu 172.16.10.10

Der gewählte Weg ändert sich, da der (nach Hop-count sortierte) kürzeste Weg nicht mehr verfügbar ist.

```
# traceroute 172.16.10.10
traceroute to 172.16.10.10 (172.16.10.10), 30 hops max, 60 byte packets
 1  _gateway (192.168.20.1)  0.155 ms  0.165 ms  0.116 ms
 2  192.168.30.2 (192.168.30.2)  0.239 ms  0.229 ms  0.276 ms
 3  10.0.0.2 (10.0.0.2)  0.369 ms  0.437 ms  0.349 ms
 4  10.0.0.6 (10.0.0.6)  0.551 ms  0.540 ms  0.557 ms
 5  172.16.10.10 (172.16.10.10)  0.789 ms  0.803 ms  0.718 ms
```

## Von 192.168.10.10 zu 192.168.0.10

Der Weg bleibt exakt gleich.

```
# traceroute 192.168.0.10
traceroute to 192.168.0.10 (192.168.0.10), 30 hops max, 60 byte packets
 1  _gateway (192.168.10.1)  0.171 ms  0.198 ms  0.211 ms
 2  10.0.0.2 (10.0.0.2)  0.224 ms  0.315 ms  0.204 ms
 3  192.168.0.10 (192.168.0.10)  0.351 ms  0.476 ms  0.490 ms
```