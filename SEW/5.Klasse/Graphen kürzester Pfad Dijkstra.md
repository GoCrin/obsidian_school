[[Dijkstra-Algorythmus]]

Ein kürzester Pfad ist ein Pfad zwischen zwei unterschiedlichen Knoten eines Graphen der die minimale Länge bezüglich der Kantengewichtsfunktion hat. Der Algorithmus von Dijkstra löst das Problem der kürzesten Pfade, indem er einen kürzesten Pfad zwischen dem gegebenen Startknoten und einem anderen Knoten in einen Kantengewichteten Graphen berechnet.

```
funktion Dijkstra (V, E, start) // Knoten, Kanten, Startknoten
	Für alle v elementIn V
		Wenn v == start
			distanz[v] := 0 // Abstand zum Startknoten
		andernfalls
			distanz[v] := unendlich
		vorgänger[v] := null
		Q.einfügen(v) // Menge der zu bearbeitenden knoten
	Solange Q nicht leer ist
		u := kleinstes aus Q // Knoten mit geringster Distanz
		Q.entferne(u)
		Für alle (u, v) elementIn E mit v elementIn Q // Für alle Nachbarknoten von u
			Wenn distanz[u] + gewicht(u, v) < distanz(v) // Neue min. Distanz?
				distanz[v] := distanz[u] + gewicht(u, v) // Ja, aktualisieren
				vorgänger[v] := u // Distanz und Vorgänger
```