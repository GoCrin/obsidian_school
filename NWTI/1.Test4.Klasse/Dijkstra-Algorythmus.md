# Vorgehen

1. Liste der unbesuchten Knoten erstellen
2. einen Startknoten `S` wählen
3. Liste der Kosten zu jedem Knoten erstellen
	* `S` bekommt Kosten: $0$
	* alle anderen Knoten bekommen Kosten: $\infty$
4. Solange es unbesuchte Knoten gibt:
	1. Den Knoten mit den kleinsten Kosten aus der Liste der unbesuchten Knoten nehmen
	2. für alle Kanten die mit dem Knoten verbunden sind:
		1. Das Gewicht vom Knoten und das des anderen addieren
		2. wenn diese Summe kleine als die Aktuellen kosten zum anderen Knoten sind wird dieser Wert mit der Summer ersetzt
	3. Den gewählten Knoten aus der Liste der unbesuchten Knoten entfernen


* den Startknoten S wählen (in dem Fall: S = A)
* Gewicht von S auf 0 setzten
* alle anderen Gewichte auf $\infty$
* solange es unbesuchte Knoten (gespeichert in U) gibt:
	* Wählen den Knoten mit kleinstem Gewicht aus U (A)
	* für alle Kanten von Gewähltem Knoten (A) zu unbesuchten Knoten
		* addieren von Gewicht von A mit Kanten Gewicht von Zielknoten
		* wenn der Wert kleiner als der aktuelle Wert ist, überschreibt man diesen.
	* Gewählten Knoten (A) aus U entfernen.



Wählen den Knoten mit kleinstem Gewicht aus V (A)
"gehen nach" B, addieren von Gewicht von A und Kanten Gewicht (2), wenn der Wert (0+2) kleiner als der aktuelle Wert ($\infty$) ist, überschreibt man diesen. Gewählten Knoten (A) aus U entfernen (jetzt: {B,C,D}).