Herunterladen der config Datei unter `https://www.vpngate.net/en/`

```shell
sudo pacman -S openvpn

sudo openvpn --data-ciphers DEFAULT:AES-128-CBC --config Downloads/vpngate_vpn855853386.opengw.net_udp_1543.ovpn
```


## Routingtabelle

```shell
ip route
```

Man sieht, dass die neue default route über `tun0` den VPN geht.

```shell
0.0.0.0/1 via 10.211.1.34 dev tun0 
default via 172.18.8.1 dev wlp5s0 proto dhcp src 172.18.10.215 metric 600 
10.211.1.34 dev tun0 proto kernel scope link src 10.211.1.33 
24.17.137.59 via 172.18.8.1 dev wlp5s0 
128.0.0.0/1 via 10.211.1.34 dev tun0 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
172.18.8.0/22 dev wlp5s0 proto kernel scope link src 172.18.10.215 metric 600 
172.19.0.0/16 dev br-42cb88a83110 proto kernel scope link src 172.19.0.1 linkdown 
```

## Ausgabe von ip a
```shell
# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether e4:a8:df:b5:ee:af brd ff:ff:ff:ff:ff:ff
    altname enxe4a8dfb5eeaf
3: wlp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether e0:0a:f6:73:26:d3 brd ff:ff:ff:ff:ff:ff
    altname wlxe00af67326d3
    inet 172.18.10.215/22 brd 172.18.11.255 scope global dynamic noprefixroute wlp5s0
       valid_lft 28029sec preferred_lft 28029sec
    inet6 fe80::e1e2:ab10:9393:d767/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: br-42cb88a83110: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 86:8e:de:61:fb:51 brd ff:ff:ff:ff:ff:ff
    inet 172.19.0.1/16 brd 172.19.255.255 scope global br-42cb88a83110
       valid_lft forever preferred_lft forever
5: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 56:97:16:d9:74:6a brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
6: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.211.1.33 peer 10.211.1.34/32 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::4abc:4be6:a236:90cf/64 scope link stable-privacy proto kernel_ll 
       valid_lft forever preferred_lft forever
```

## Wireshark

Kommunikation zwischen mir und etwas

![[Pasted image 20260319120714.png]]



![[Pasted image 20260319120628.png]]

## warum existiert die Seite vpngate.net?

Weil eine Uni in Japan "Global Distributed Public VPN Relay Servers" untersuchen will.

## aus welchen Ländern kommt die überwiegende Zahl der User?  
Die meisten Nutzer kommen aus Iran

## was ist TCP Meltdown im Bezug auf VPNs?

Wenn TCP über TCP getunnelt wird sorgt das für performance Probleme, weil dieses doppelte TCP für Pakete überkompensiert.

## warum sollte man lieber UDP als TCP als Transportprotokoll für OpenVPN verwenden?

Damit TCP Meltdown nicht passiert.

---

Quellen:
[vpngate (19.3.26)](https://www.vpngate.net/) (insbesondere die FAQ)
[openvpn.ne (19.3.26)](https://openvpn.net/as-docs/faq-tcp-meltdown.html#understanding-tcp-meltdown-in-access-server)