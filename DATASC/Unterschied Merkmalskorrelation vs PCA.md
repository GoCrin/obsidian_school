Merkmalskorrelation vs. PCA

# Merkmalskorrelation
Wenn nur wenige Variablen z.B. 2, wie Körpergröße und Schuhgröße welche stark korrelieren dann eine der beiden entfernen

# PCA
Wenn Datensatz mit vielen Variablen, mit vielleicht komplexen Beziehungen, dann hilft PCA die Hauptkomponenten zu identifizieren, welche die größte Varianz haben.

>Kurz gesagt: PCA ist präziser

Hinweis: PCA kann nur mit Zahlenwerten umgehen → One-Hot-Encoding
Konkretewerte werden nebeneinander dargestellt, wenn der Wert zutrifft 1, sonst 0

AUS

| Maps     | Zeit | Fuß / Öffi / Auto |
| -------- | ---- | ----------------- |
| Strecke1 |      |                   |
| Strecke2 |      |                   |
WIRD:


| Maps     | Zeit | Fuß | Öffi | Auto |
| -------- | ---- | --- | ---- | ---- |
| Strecke1 |      | 0   | 1    | 0    |
| Strecke2 |      | 1   | 0    | 0    |