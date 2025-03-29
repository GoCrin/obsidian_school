~/.ssh/config
Host    dhcp
        Hostname localhost
        user user
        Port 6223
        IdentityFile C:\Users\linus\Documents\Schule\2024-25\SYT\mykeys\id_3bhits_rsa

Ermöglicht kürzeren Befehl um sich via ssh zu verbinden.
`ssh dhcp`
new-alias d .\sshDhcp.ps1 -f