Man schickt icmp v6 nachricht an eine bestimmte multicast Adresse.
solicited node address

 ping an link local geht ohne interface nicht, weil es das gleich sub netz mehrmals gibt

# Stateless IPv6 generation

SLAAC
stammt von EUI-64 (welches die Interface ID durch die mac Adresse generiert)

## EUI-64

A 48-bit MAC can be transformed to an 64-bit interface ID by inverting the 7th (universal) bit and inserting a ff and fe byte after the 3rd byte. So the MAC `00:03:ba:24:a9:c6` becomes `0203:baff:fe24:a9c6`. See RFC 4291 Appendix A and RFC 4941.

![[Pasted image 20260129105321.png]]

Mit dem verfahren wäre die Interface id immer gleich, was mit Blick auf Datenschutz nicht gut ist. Wenn man sich einmal über diese IPv6 Adresse authentifiziert kann immer wieder egal in welchem LAN erkennen, dass man diese Person ist. 
Der Subnetprefix (1. 64 bit) hängt vom aktuellen LAN in dem man ist

## SLAAC
man generiert eine addrese und schickt eine neighbor discovery and dieser Adresse

Man generiert eine link local Adresse und fragt im Netz welche mac adresse der rechner mit der IPv6 hat (neighbor discovery), wenn keiner antwortet nimmt man diese IPv6 Adresse.

Mit einer Router solicitation schickt man ein icmpv6 Paket an alle Router, diese antworten und geben einen (glaub ich!) den Subnetprefix & co 