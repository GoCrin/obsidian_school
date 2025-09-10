Um eine hohe Qualität der auszuliefernden Software sicherzustellen ist es notwendig diese intensiv zu testen
#### White-Box-Test vs. Black-Box-Test
##### White-Box
![[Pasted image 20250219084106.png]]
Das Testen erfolgt mit Blick auf die implementierte Logik.
<u>Vorteile</u>:
* Die interne Funktionsweise kann komplett getestet werden.
* Gut automatisierbar durch Testtool (z.B. JUnit)
<u>Nachteile</u>:
* Eventuell Testen um "Fehler herum"
* Erfüllung der gesamten Spezifikation wird nicht überprüft.
##### Black-Box
![[Pasted image 20250219084243.png]]
Nur nach außen sichtbares Verhalten fließt in den Test ein.
<u>Vorteile</u>:
* Gute Verifikation der gesamten Anwendung
* Testen ist unabhängig von der Programmiersprache
<u>Nachteile</u>:
* Neuer Code wird nur durch Zufall geteilt
* Schlecht / Schwer automatisierbar