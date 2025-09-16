```Bash
ping 8.8.8.8
```
1. macht ein ICMP Paket
	* Header
		* Type = ECHO_REQUEST
		* Code = 0
	* ICMP Payload
2. IP-Header
	* Src-IP wird über Routingtabelle herausgefunden
3. Ethernet-Header

## Routingtabelle
* Dest-Addresse
	* Meist Subnetze
	* 0.0.0.0/0 -> Default Route auf vielen Endgeräten
* Next hop / Gateway
	* Wem gibt man das IP-Paket
* Metrik
	* Kosten / Bewertung für Routen