# Penetrations-testing 
## 1 Erstellung der virtuellen Umgebung
### 1.1 Herunterladen der virtuellen Maschinen

* Kali-Linux
* metasploitable3-ub1404upgraded -> https://sourceforge.net/projects/metasploitable3-ub1404upgraded/files/Metasploitable3-ub1404.ova/download
* Metasploitable -> https://sourceforge.net/projects/metasploitable/

### 1.2 Maschinen in Virtualbox importieren

Alle 3 Maschinen werden in Virtualbox importiert, dann werden sie in alle in ein NAT-Netzwerk gesetzt.

### 1.3 Anmeldung an die virtuellen Maschinen

Alle Maschinen werden gestartet und es wird sich mit den folgenden Nutzerdaten angemeldet.

| Maschine                       | Nutzername | Passwort |
| ------------------------------ | ---------- | -------- |
| Kali-Linux                     | kali       | kali     |
| metasploitable3-ub1404upgraded | vagrant    | vagrant  |
| Metasploitable                 | msfadmin   | msfadmin |

## 2 Anwendung von nmap

### 2.1 Scannen des Netzwerks

In der Kali-Linux virtuellen Maschine wird folgender Befehl abgesetzt um die im Netz aktiven Geräte und deren IPv4 Adressen anzuzeigen. 

```bash
sudo nmap -sn 10.0.2.0/24
```

Dieser liefert unter anderem die 2 weiteren Maschinen. zum Zeitpunkt der Erstellung dieses Dokuments sind deren IP's wie folgt.

| Maschine                       | IPv4        |
| ------------------------------ | ----------- |
| metasploitable3-ub1404upgraded | `10.0.2.15` |
| Metasploitable                 | `10.0.2.4`  |
### 2.2 Weitere Informationen über die Matasploitable-Maschinen herausfinden

Das `nmap` Argument `-A` findet weiter Eigenschaften über das Betriebssystem des Rechners heraus.

```Bash
nmap -A 10.0.2.15
```

dieser Befehl gibt folgendes auf der Konsole aus.

```
Starting Nmap 7.95 ( https://nmap.org ) at 2025-10-23 08:06 EDT
Nmap scan report for 10.0.2.15
Host is up (0.00020s latency).
Not shown: 991 filtered tcp ports (no-response)
PORT     STATE  SERVICE     VERSION
21/tcp   open   ftp         ProFTPD 1.3.5
22/tcp   open   ssh         OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 2b:2e:1f:a4:54:26:87:76:12:26:59:58:0d:da:3b:04 (DSA)
|   2048 c9:ac:70:ef:f8:de:8b:a3:a3:44:ab:3d:32:0a:5c:6a (RSA)
|   256 c0:49:cc:18:7b:27:a4:07:0d:2a:0d:bb:42:4c:36:17 (ECDSA)
|_  256 a0:76:f3:76:f8:f0:70:4d:09:ca:e1:10:fd:a9:cc:0a (ED25519)
80/tcp   open   http        Apache httpd 2.4.7 ((Ubuntu))
|_http-server-header: Apache/2.4.7 (Ubuntu)
|_http-title: Index of /
| http-ls: Volume /
| SIZE  TIME              FILENAME
| -     2020-10-29 19:37  chat/
| -     2011-07-27 20:17  drupal/
| 1.7K  2020-10-29 19:37  payroll_app.php
| -     2013-04-08 12:06  phpmyadmin/
|_
445/tcp  open   netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
631/tcp  open   ipp         CUPS 1.7
|_http-title: Home - CUPS 1.7.2
|_http-server-header: CUPS/1.7 IPP/2.1
| http-methods: 
|_  Potentially risky methods: PUT
| http-robots.txt: 1 disallowed entry 
|_/
3000/tcp closed ppp
3306/tcp open   mysql       MySQL (unauthorized)
8080/tcp open   http        Jetty 8.1.7.v20120910
|_http-server-header: Jetty(8.1.7.v20120910)
|_http-title: Error 404 - Not Found
8181/tcp closed intermapper
MAC Address: 08:00:27:8B:2B:30 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Aggressive OS guesses: Linux 3.2 - 4.14 (98%), Linux 3.8 - 3.16 (98%), Linux 3.10 - 4.11 (94%), Linux 3.13 - 4.4 (94%), Linux 3.13 (94%), OpenWrt Chaos Calmer 15.05 (Linux 3.18) or Designated Driver (Linux 4.1 or 4.4) (94%), Linux 4.10 (94%), Android 5.0 - 6.0.1 (Linux 3.4) (94%), Android 8 - 9 (Linux 3.18 - 4.4) (94%), Linux 3.2 - 3.10 (94%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
Service Info: Host: METASPLOITABLE3-UB1404; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)
|   Computer name: metasploitable3-ub1404
|   NetBIOS computer name: METASPLOITABLE3-UB1404\x00
|   Domain name: \x00
|   FQDN: metasploitable3-ub1404
|_  System time: 2025-10-23T12:06:44+00:00
|_clock-skew: mean: 1s, deviation: 2s, median: 0s
| smb2-time: 
|   date: 2025-10-23T12:06:43
|_  start_date: N/A
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required

TRACEROUTE
HOP RTT     ADDRESS
1   0.20 ms 10.0.2.15

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 58.10 seconds
```

Dieser Befehl wird ein weiteres mal mit der IP des 2. Rechners aus geführt.

```Bash
nmap -A 10.0.2.4
```

Man erhält eine ähnliche Antwort wie beim ersten Rechner.

