```
Install-WindowsFeature DNS -IncludeManagementTools
```

tools -> DNS
DNS-Server konfigurieren
RMB -> neue Zone
	weiter
	primäre zone
	forward lookupzone
	zonenname: 3bhits.local
	neue datei mit diesem namen erstellen
	dynamische updates nicht zulassen

Foward-Lookupzonen
	3bhits.local
	RMB -< neuer host
	www
	ipaddr: irgendwas (z.B 10.0.2.12)
	hosthinzufügen

www (geht auf) -> 10.0.2.12

im DHCP-Server muss nun der DNS-Server vergeben werden
