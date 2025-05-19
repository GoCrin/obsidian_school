Datum: 8.5.25
## Beschreibung
Installation des IIS unter Windows 

- Eigene Homepage mittels PHP erstellen (index.php)
- Ausgabe auf der Webseite von "Hello World"  bei Aufruf der Seite
- Konfiguration damit die Seite über php.3bhtis.local aufrufbar ist
- notwendige config für IIS

## KA
Im Server-Manager
* Verwalten
* Rollen und Features hinzufügen
* 3x weiter
* Features hinzufügen
* so oft "weiter" wie geht
* Installieren
* **nach Installation!!** schließen

Konfiguration (als Start wieder Server-Manager)
* Tools
* Internetinformationsdienste (IIS)-Manager
* Win-... aufklappen
* Websites aufklappen
* RMB (rechte Maustaste) auf Websites
* Webseite hinzufügen
* Sitename: z.B. "aufgabe"
* Physischer Pfad: irgendeiner (sollte wahrscheinlich leerer Folder sein)
* Bindung:
	* Typ: http
	* IP-Addresse: eigene
	* Port: 80
	* Hostname: php.3bhtis.local
* C: