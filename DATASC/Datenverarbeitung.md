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

Standardmäßig wird Kopie erstellt mit inplace = True wird die Spalte aus dem urspünglichen df gelöscht.