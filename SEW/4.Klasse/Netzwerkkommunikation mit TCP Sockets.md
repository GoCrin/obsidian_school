TCP ist ein verbindungsorientiertes Protokoll (siehe Gegenstand Netzwerktechnik). Zwischen Client und Serverprozess wird eine virtuelle Verbindung aufgebaut über die durch einen bidirektionalen Datenstrom Daten ausgetauscht werden.
Zu dem Zweck wird sowohl auf Client- als auch auf Serverseite ein sogenannter "Socket" erstellt.

![[Pasted image 20250917122729.png]]

Konkrete Implementierung siehe Demo Programm.
Damit ein Server mit mehreren Clients gleichzeitig kommunizieren kann, verwendet man Threads.