Ein Graph ist eine Struktur, die aus einer Menge von Knoten (Nodes, Vertices) und einer Menge von Kanten (Edges) besteht:
$$V = \{v_1, v_2, ..., v_n\}$$
$$E = \{e_1, e_2, ..., e_m\}$$
→ Graph $G = \{V,E\}$
z.B.
![[Pasted image 20260915140034.png]]

Mittels Graphen kann z.B. beschrieben werden:
- Netzwerktopologien
- Straßenverbindungen zwischen Städten
- Rohleitungssysteme
- ...

Anwendungsbereiche (Algorithmen):
- Routenplanung (kürzester Weg zwischen Knoten)
- kürzeste Rundreise (Problem des Handelsreisenden)
- Netzwerkrouting (Pakete)

Mögliche Eigenschaften von Graphen:
- **Ungerichteter vs. Gerichteter Graph:** Endet die Kante zwischen zwei Knoten mit einem Pfeil, so spricht man von einem gerichteten Graphen ansonsten von einem ungerichteten Graphen.
- **Gewichtet:** Ein gewichteter Graph ist ein Graph, dessen Kanten ein Gewicht (numerischer Wert) zugewiesen ist.

![[Pasted image 20260915142837.png]]
(Gewichtet und gerichtet)

- **Zyklischer Graph:** Ein Zyklus ist ein Kantenzug mit unterschiedlichen Kanten bei dem Start- und Endknoten gleich sind. Ein zyklischer Graph ist ein Graph mit mindestens einem Zyklus.
- **Zusammenhängender Graph:** Ein Graph heißt, wenn es von jedem knoten einen Weg zu jedem anderen Knoten gibt.