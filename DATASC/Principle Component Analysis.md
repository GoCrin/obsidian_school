Principle Component Analysis (PCA) noch eine weitere wesentliche Methode um Dimensionen zu Reduzieren

weniger Dimensionen => Algorithmus effizienter

PCA hilft aussagekräftigsten dimensionen zu finden

Nebendedingung bei winigen dimensionen PCA nicht verwenden

Funktionsweise
1. **Zentrierung der Daten**, dadurch brauchen wir den mittelwert nicht mehr (bei unterschiedlichen größenordnungen noch standardisieren)
2. **Berechnung der Kovarianzmatrix**, die Kovarianzmatrix beschreibt die Abhängigkeit zwischen den Variablen
	1. hoch positiv => Merkmale bewegen sich miteinander
	2. nahe 0 => Daten bewegen sich unabhängig
	3. hoch negativ => bewegen sich gegengleich
3. **Eigenwertzerlegung der Kovarianzmatrix** neue Richtungen (Eigenvektoren) Werden gefunden, entlang derer die Daten eine größere Varianz zeigen (3D-Bild zu aussagekräftigsten 2D-Bild)![[Pasted image 20261012194024.png]]
4. **Auswahl der Hauptkomponenten**, Eigenvektoren mit den höchsten Eigenwerten werden die "neuen" Koordinatenachsen
5. **Transformation der Daten**, die Daten werden auf den neuen Raum der Hauptkomponente "projiziert"


---

"Pasted image 20261012194024.png" - von: [@raghavan99o: Principal component analysis (PCA): Explained and implemented](https://medium.com/@raghavan99o/principal-component-analysis-pca-explained-and-implemented-eeab7cb73b72)
