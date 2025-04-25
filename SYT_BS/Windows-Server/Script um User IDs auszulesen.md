$a = Get-DhcpServerv4Lease -ScopeId 10.0.2.0 | Where-Object Hostname -like debian | select ClientId
$a.ClientId
Add-DhcpServerv4Reservation -ScopeId 10.0.2.0 -IPAddress 10.0.2.55 -ClientId $a.ClientId -Description "Testreservierung" -Name "DebianTest"
Get-DhcpServerv4Reservation -ScopeId 10.0.2.0

Geht nicht
Set-DhcpServerv4Reservation -IPAddress 10.0.2.55 -ClientId $a.ClientId -Description "Testreservierung" -Name "Debian"
Remove-DhcpServerv4Reservation -ScopeId 10.0.2.0 -ClientId $a.ClientId
