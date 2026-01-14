# Vorgehen

1. Liste der unbesuchten Knoten erstellen
2. einen Startknoten `S` wählen
3. Liste der Kosten zu jedem Knoten erstellen
	* `S` bekommt Kosten: $0$
	* alle anderen Knoten bekommen Kosten: $\infty$
4. Solange es unbesuchte Knoten gibt:
	1. Den Knoten mit den kleinsten Kosten aus der Liste der unbesuchten Knoten nehmen
	2. für alle Kanten die mit dem Knoten verbunden sind:
		1. Die Kosten vom gewählten Knoten mit den Kosten der Kante addieren
		2. wenn diese Summe kleiner als die Aktuellen Kosten des anderen Knoten ist, wird dieser Wert mit der Summer ersetzt
	3. Den gewählten Knoten aus der Liste der unbesuchten Knoten entfernen

Dieser pseudo code, ist der im Unterricht implementierte. Er liefert nur die Kosten zu jedem Knoten vom Startknoten aus. Der Weg zu jedem Knoten ist nicht bekannt.

# Übung

| Knoten | Init | Runde 1 | Runde 2 | Runde 3 | Runde 4 | Runde 5 | Runde 6 | Runde 7 | Vorgänger |
| ------ | ---- | ------- | ------- | ------- | ------- | ------- | ------- | ------- | --------- |
| a      |      |         |         |         |         |         |         |         |           |
| b      |      |         |         |         |         |         |         |         |           |
| c      |      |         |         |         |         |         |         |         |           |
| d      |      |         |         |         |         |         |         |         |           |
| e      |      |         |         |         |         |         |         |         |           |
| f      |      |         |         |         |         |         |         |         |           |
| g      |      |         |         |         |         |         |         |         |           |
| h      |      |         |         |         |         |         |         |         |           |
| i      |      |         |         |         |         |         |         |         |           |