Datenanalyse
Fehler in größeren Datensätzen

Beim maschinellen Lernen und als Data Scientist geht es darum Daten zu verstehen, wie sie sich verhalten, wie sie verteilt sind usw.

Daten **normalisieren**
- ungefähr gleich verteilt (Datenpunkte in gleichen Abstände) MinMaxScaler
- normal verteilt (Nach Gauskurve verteilt) StandardScaler

Bereinigen kann bedeuten:
- Duplikate entfernen
- fehlende Werte (empty cells) finden und ändern
- Ausreißer finden
- Korrelationen aufdecken

dataframe - df.dropna()
df.dropna(how='all')
df.fillna(0)

Kaggle (von Google)

Was liefert df.describe()

Wiederholung **Mittelwert** vs **Median** und die Quartile

Visualisierungen
ScatterPlot (Streudiagramm)

dann Histogramm
Bsp Rechnungen
Verschiedene Kübel, man Gruppiert auf irgendeine Arte seine Dinge. z.B nach Preis: <=100, <200, <300, usw

Manchmal gibt es Spalten, welche nicht gewünscht werden

```python
df = df.drop('Spaltenname', axis=1)
```

Standardmäßig wird Kopie erstellt mit inplace = True wird die Spalte aus dem urspünglichen df gelöscht

# Principle Component Analysis

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
3. **Eigenwertzerlegung der Kovarianzmatrix** neue Richtungen (Eigenvektoren) Werden gefunden, entlang derer die Daten eine größere Varianz zeigen (3D-Bild zu aussagekräftigsten 2D-Bild)
4. **Auswahl der Hauptkomponenten**, Eigenvektoren mit den höchsten Eigenwerten werden die "neuen" Koordinatenachsen
5. **Transformation der Daten**, die Daten werden auf den neuen Raum der Hauptkomponente "projiziert"

