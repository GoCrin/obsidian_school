#

Von Microsoft um alle ihrer Produkte zu Administrieren 

```Powershell
Install-Module Microsoft.Graph
```
Um das Graph Modul zu installieren

```Powershell
Connect-MgGraph -Scopes User.Read.All
```
Um sich zu Verbinden

# Automatisierung

Um Graph Aktionen zu Automatisieren muss bei Microsoft eine Applikation erstellt werden, welche ein Zertifikat braucht

## Zertifikat generieren

```Bash
openssl req -new -newkey rsa:4096 -out cert.req
openssl x509 -req -in cert.req -out cert.pem
```
Um ein Zertifikat zu erstellen

```Bash
openssl pkcs12 -in cert.pem -inkey key.pem -out syt.pfx -export
```
