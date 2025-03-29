## 1. Aufgabe
* Client-IP-Netze für Wien, Graz und Linz bestimmen
* Subnet-Mask für Clientnetze bestimmen
* IP-Konfiguration der Notebooks in den Clientnetzen
* Datei speichern unter "3BHITS_NWT_Lichtenwallner_20250303"
* Hostname von Router & Switch ändern
* Allen Router-Interfaces die entsprechenden IP-Adressen zuweisen

**Clientnetze:** 10.16.1.0/24

Wien: 100 Hosts -> Netz-IP: 10.16.1.0 /25
Graz: 50 Hosts -> Netz-IP: 10.16.1.128 /26
Linz: 50 Hosts -> Netz-IP: 10.16.1.192 /26




**Linknetze:**
LN01: Wien(1) - Graz(2)
LN02: Graz(1) - Linz(2)
LN03: Linz(1) - Wien(2)