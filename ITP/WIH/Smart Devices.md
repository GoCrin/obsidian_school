Ist ein kleines elektronischen Gerät (thing) misst und leitet Daten weiter.

# LoraWAN
Long Range WAN
Normale Frequenzbereiche dürfen nicht einfach verwendet werden
Spezielle (Kontinent / Land /... abhängig EU 868) sind aber Leistungsbeschrenkt
Lora umgeht das mit geringen Übertragungsraten
Ist Netzzugriffs schicht auf funkschicht
LoraWAN geht vom Smartdevice bis zu einem Gateway (danach IP)

Geräteklassen
Class A: sendet macht danach ein Empfangsfenster auf
Class B: nach senden und in periodischen abständen
Class C: empfängt immer außer beim senden

Over the air activation OTAA
activation by personalization ABP

AT-Befehle
AT für attention
TheThingsNetwork.org

MQTT
Protokoll
Clients können nicht untereinander kommunizieren sondern nur mit einen Broker
Clients können gewisse Topics abonnieren
Single-Level-Wildcard: +
Multi-Level-Wildcard: \#

MQTT QoS (Quality of Service)
0 Fire an forget
1 Acknowledgement
2 exactly once
