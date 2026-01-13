Dient als Unterlage für die Wiederholung in der 2. Woche. Wie es in den jeweiligen Überschriften steht, sind 2 Kapitel zu (fast) 100% in jedem Test.

Lebenszyklus einer activity ist für die Wiederholung nicht zu Lernen.

# Gründe für Verwendung
* Open-Source
* Viele Geräte Hersteller
* Wird oft verwendet

# Android Stack (100% im Test)

![[Pasted image 20251217190702.png]]

# Von Java-Code zu Dalvik VM (100% im Test)

![[Pasted image 20251217190815.png]]

# Dalvik VM vs. ART VM

Dalvik macht **Just in Time** und ART macht **Ahead of Time**

# Android Komponenten

* **Activity**: zur Darstellung und Verwaltung von Oberfächen
* **Service**: erledigt Hintergrundprozesse
* **Content Provider**: für Datenverwaltung (abstrahiert die "Presistenzschicht" -> 1:1 das selber aber in "smart")
* **Broadcast Receiver**: Lässt dich auf Systemnachrichten reagieren

# Sandbox

* Android Sandboxed alle Anwendungen
* Sandbox ist eingeschränkte Laufzeitumgebung

# Signieren von Anwendungen

* (via Zertifikat)
* stellt nur sicher, das mehrere Apps vom selben Hersteller sind

# Berechtigungen

Braucht man um Sachen außerhalb der Sandbox zu verwenden/machen

# Oberflächengestaltung

* **View**: Alles was man sieht -> TextInput, Buttons, Listen,... (je eine View)
* **Layout**: Ordnet Views am Bildschirm an
* **Activity**: Verwaltet und stellt Oberflächen da