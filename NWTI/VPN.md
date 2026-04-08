Virtual private network

Tunneling

Rechner verbindet sich über unsicheres Medium mit einem LAN. Über einen Tunnel kann mit Blick auf die Funktionalität die selbe Qualität erreicht werden als ob man physisch im LAN wäre.

Software Lösung
Kann funktionieren, ist aber als Applikation nicht "tief genug im System" um wirklich zu garantieren, dass man einen Tunnel verwendet

Hardware
Laptop geht in Tunnelschnittstelle diese stellt sicher, dass man mit der Tunnelschnittstelle vom Ziel LAN verbunden ist.

VPN Anbieter
Diese Werben damit über eine VPN-Verbindung Geoblockings zu umgehen. Teilweise werben Sie auch mit Sicherheit im Internet (weil Verbindung ist verschlüsselt)

VPN Anbieter selber spielen
(Links sind nicht Teil des Stoffes :) )
https://www.wireguard.com/install/
https://github.com/WeeJeWel/wg-easy

## Übung VPN-Gate

[vpngate](https://www.vpngate.net/en/)

```shell
sudo pacman -S openvpn
```

[settings download](https://www.vpngate.net/common/openvpn_download.aspx?sid=1773915001148&udp=1&host=vpn855853386.opengw.net&port=1543&hid=25537948&/vpngate_vpn855853386.opengw.net_udp_1543.ovpn)