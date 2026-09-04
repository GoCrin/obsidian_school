![[Pasted image 20260616081049.png]]
Ziel ist es Backups der Konfigurationen der 2 Geräte (R1 & S1) auf den Debian Rechner zu speichern.

# RouterOS / Mikrotik

`export`zeigt was auf dem Gerät konfiguriert wurde. `print` zeigt den tatsächlichen Zustand des Gerätes.


```
/export show-sensitive file=config.rsc
/system/backup/save name=test.rsc
```

Übertragen der Config auf den Rechner, in dem man mit scp auf dem Rechner 
```
scp id .rsra admin@<ip>:/config.rsc ./ 
```
Fragt nach Password, wenn eines gesetzt ist. Dies ist schwer automatisierbar, weshalb jetzt die Authentifizierung mittels SSH-Keys eingestellt 
/user

```
crontab -e
```
```

```

# Cisco

Verwendet `tftp`, welches immer Client und Server hat. Der Client muss den Dateitransfer starten.

```

```

```
en
show run
```

am Debian
```
tftp-hpa
cd /svr/tftp
tftp <ip>
# Im menu

```

```bash
#!/bin/bash

#Mikrotik - scp / ssh
DATESTRING=`date "+%Y%m%d-%H%M%S"`
ssh admin@<ip> export show-sensitive > /home/debian/$DATESTRING-config_R1.conf

# Cisco - tftp
tftp <ip> -c get vlan.dat /home/debian/$DATESTRING-vlan.dat
tftp <ip> -c get startup-config /home/debian/$DATESTRING-startup-config
```

am Switch
```
startup-config tftp:<ip>/ciscoswitch.conf
copy nvram:vlan.dat tftp://<ip>/vlan.dat

tftp-server nvram:vlan.dat
tftp-server nvram:startup-config
```

Macht (5) virtuelle Terminals (wurd nicht erklärt warum oder wie, oder wofür)
```
line vty 0 4
```

```

```

