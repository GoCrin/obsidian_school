Spanning Tree Protocol (STP)

Was ist der Zentrale Punkt im Netzwerk (Route-Bridge)? Es setzt diesen Punkt zufällig. Priority (vom admin) und mac des switches werden zusammen "gerechnet" (prio concat. mac), und die mit dem niedrigsten Wert wird zur Route-Bridge.

STP ist standardmäßig aktiv, weshalb man auf jedem switch die gewünschte Priority setzten sollte.

Die Route-Bridge ist nur relevant, wenn das Netz nicht schleifenfrei ist.

Bei STP kann für jedes Interface Kosten definiert werden. Wichtig, wenn man standardmäßig die schnellste Verbindung aktiv haben will.

---

Günstigste Wege zur Route-Bridge werden berechnet.
# Switching loops

Wenn zwischen Switches ein "Ring" ist, sorgen diese dafür, dass Frames unendlich lange im Kreis geschickt werden. Bei besonders ungünstigen Verkabelungen wächst die Anzahl an Frames exponenziell und verbraucht somit nach kurzer Zeit die gesamte Bandbreite.