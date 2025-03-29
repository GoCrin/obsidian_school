Root123
^ Passwort
## Voraussetzungen

* Fixe IP-Adresse

## Graphisch


## CMD

```
Install-WindowsFeature DHCP -IncludeManagementTools
Add-DhcpServerv4Scope -Name "Was ich will" -StartRange 10.0.2.100 -Endrange 10.0.2.200 -SubnetMask 255.255.255.0
Get-Service | Where-Object { $_.Name -ilike "*dhcp*" }
Get-DhcpServerv4Scope

```
Window-Dhcp standard ist es den ganzen IP Bereich in range einzustellen und dann mit Exclusionranges addressen auszunehmen.
Diese Ausgenommenen IPs sind für Geräte die auch ohne, dass der DHCP-Server funktioniert eine IP brauchen
```
Add-DhcpServerv4ExclusionRange -ScopeId 10.0.2.0 -StartRange 10.0.2.150 -EndRange 10.0.2.200
Set-DhcpServerv4OptionValue -ScopeId 10.0.2.0 -Router 10.0.2.1 -DnsServer 10.0.2.5 -force
Get-DhcpServerv4OptionValue -ScopeId 10.0.2.0
Get-DhcpServerv4Lease -ScopeId 10.0.2.0 | Format-List
```

Warum Client-Id
Weil cloud computing: dadurch, dass diese Maschinen irgendwo mit irgendwelcher Hardware gestartet wird. Wenn man will, dass die IP-reservierung die selbe bleibt kann man sich nicht auf mac-addresse verlassen.

```
Add-DhcpServerv4Reservation -ScopeId 10.0.2.0 -IPAddress 10.2.0.50 -ClientId <ID> -Name <NAME>
```