Proxmox bietet einen Free to use Hypervisor aus Österreich.

Zentraler Punkt: Storage, wo sollen die Festplatten der virtuellen Gräte liegen und in welcher Form.
1 Möglichkeit: Storage im Server selbst.
2 Möglichkeit: Storage getrennt vom Server (SAN Storage Area Network, Festplatte über Glasfaser = fiber channel), Schwierigkeit die art wie die Daten gespeichert sind, muss shared filesystem sein, weil mehrere Maschinen gleichzeitig zugreifen. Es muss also culster aware sein. 

Level: stellt es dem hypervisor Blöcke (wie eine wirkliche Festplatte) oder file (Also Dateien)
Shared: ist es dafür gedacht, dass mehrere gleichzeitig darauf zugreifen
Snapshots: Kann man den zustand einer virtuellen Maschine speichern

festplatten auf raid none
zfs 1

LACP auf linux (nic0, nic1)
virtuellen switch der vlan aware ist
2 virtuelle Maschinen (in unterschiedlichen vlans)

- NetworkManager (graphisch oder /etc/NetworkManager)
- ifup /etc/network/interfaces
- netplan