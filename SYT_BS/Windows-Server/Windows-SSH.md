
Windows Powershell öffnen und schauen ob sshd da ist
```
Get-Service sshd
Start-Service sshd
Set-Service sshd -StartupType 'Automatic'

ssh Administrator@localhost
```

### Port forwarding

SOLLTE MAN WISSEN

### Firewall settings

**Windows Defender Firewall mit erweiterter Sicherheit**

* eingehende Regeln
* Neue Regel
* Port 22

### Key verwenden für Authentifizierung

**Für normale Nutzerkonten**
```
ssh-keygen
scp
cp "nach ~/.shh/authorized_keys"
```

**Für Administratoren**
```
cat .\key.pub >> C:\ProgramData\ssh\administrators_authorized_keys
```
