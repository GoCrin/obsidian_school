# Kali installieren
# nmap ausprobieren


# Doku zeugst
# Erstellen einer Arbeitsumgebung

## Herunterladen der Notwendigen Dateien

Für diese Penetration-Test-Umgebung werden folgende 3 Dateien / Archive heruntergeladen.

1. Ein beliebiges [kali-linux](https://www.kali.org/) in diesem Fall eines für [VirtualBox optimiertes](https://www.kali.org/get-kali/#kali-virtual-machines)
2. [metasploitable3-ub1404upgraded](https://sourceforge.net/projects/metasploitable3-ub1404upgraded/)
3. [metasploitable](https://sourceforge.net/projects/metasploitable/)

## Einbinden der heruntergeladenen Dateien

Die fertige Kali-Linux-Maschine kann in VirtualBox (VB.) durch das Drücken des "Open"-Knopf und dann das Suchen der heruntergeladenen `.vbox` Datei hinzugefügt werden.

"metasploitable3-ub1404upgraded" kann in VB. über `Home` -> `Import` hinzugefügt werden.

Es wird eine neue virtuelle Maschine erstellt, dieser wird kein ISO-Image zugewiesen. Der Erstellungsprozess wird wie gewohnt durch geführt, bis auf den Festplattenspeicher, welcher nicht erstellt wird, sondern von dem heruntergeladenen "metasploitable" bereitgestellt wird.

Es werden nun alle erstellten Maschinen in ein `NAT-Network` gesetzt.