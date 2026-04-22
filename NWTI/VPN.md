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

tls -> transport layer secure
setzt auf TCP auf

DTLS (Datagramm): UDP

OpenVpn verwendet tls

Wireguard: rennt auf UDP Port schickt aber IP Pakete

Site-to-Site: zB 2 Firmenstandorte haben einen secure tunnel zwischen einander
RoadWarrior: zB Mitarbeiter sitzt in irgendeinem Kaffee und verbidet sich zum Firmennetz

```
/interface/wireguard/add
/ip/address/add address=1.0.0.2
/interface/wireguard/peers/add allowed-address=192.168.20.0/24 endpoint-port=32903 interface=wg1 public-key="..."
```

Router 1
```
/interface wireguard add name=wg0 listen-port=13231

/ip address add address=10.10.10.1/24 interface=wg0

/interface wireguard peers add \  
interface=wg0 \  
public-key="PUBLIC_KEY_SITE2" \  
endpoint-address=10.0.0.1 \  
endpoint-port=13231 \  
allowed-address=192.168.20.0/24 \  
persistent-keepalive=25

/ip route add dst-address=192.168.20.0/24 gateway=wg0
```

Router 2
```
/interface wireguard add name=wg0 listen-port=13231  
/ip address add address=10.10.10.2/24 interface=wg0
/interface wireguard peers add \  
interface=wg0 \  
public-key="PUBLIC_KEY_SITE1" \  
endpoint-address=10.0.0.2 \  
endpoint-port=13231 \  
allowed-address=192.168.10.0/24 \  
persistent-keepalive=25
/ip route add dst-address=192.168.10.0/24 gateway=wg0
```



Es gibt 2 Anwendungsfälle für vpns

alle

## RoadWarrior

Ein Mitarbeiter hat einen vpn tunnel zu dem Netzwerk des Unternehmens 

Am Unternehmensstandort läuft die Software am router oder einem Server
Beim Mitarbeiter läuft die Software direkt auf dem Client-Rechner
## Site-to-Site

Clients sehen diese verbindung nicht

Ein tunnel zwischen 2 Firmenstandorten wird gebildet.

Die Software läuft auf beiden Seiten auf einem Netzwerkgerät (Router, ...).

## Verwendungszwecke

* sichere verbindung in ein netzwerk
* geoblockings umgehen (Netflix, eingeschränkte Meinungsfreiheit, ...)
* lokale sperren umgehen

vpn dummy will, das vpn clients im selben subnetz sind wie die im hin getunnelten Netzwerk (damit die kommunizieren können). Das wird nicht funktionieren, weil antworten an die vpn clients für einen arp broadcast sorgen, dieser wird jedoch nie auf die andere seite des tunnels kommen. Die Lösung dafür ist es ein eigenes subnetz für die VPN-Clients zu erstellen und zwischen den Netzen zu routen

# IpSec / L2TP

l2tp (layer 2 tunneling protocol) hat keine verschlüsselung -> tunnel != verschlüsselung
Deshalb wird IpSec benötigt 