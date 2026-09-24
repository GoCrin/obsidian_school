# Überwachtes Lernen
Trainingdata hat auch das Ergebnis

# Unüberwachtes Lernen (unsupervised)
Es liegen nur Daten ohne Ergebnis vor. Der Algorithmus sucht Muster und Zusammenhänge in den Daten -> Clusterbildung

# Verstärkendes lernen (reinforcement)
Ziel wird vorgegeben, z.B. Punktemax. in einem Spiel. Es wird versucht Punkte zu maximieren bzw., schlechte Entscheidungen zu vermeiden.

![[Pasted image 20260922081032.png]]
alle Merkmalsvektoren sind ein Datensatz

Film Merkmale:
- Pointen
- Länge
- Genre
- Regisaur
- Altersfreigabe

Alle Merkmale sind ein Merkmalvektor oder Featurevector
+ Label (Ergebnis, z.B gefällt mir gefällt mir nicht)

1.Bsp
=> überwachtes Lernen
v = <a_0, a_1, a_n-1, l>

2.Bsp
=> unüberwachtes lernen (label fehlt)
v = <a_0, a_1, a_n-1>

3.Bsp
Mühle Spiel: Pluspunkte für jeden gegnerischen Stein
Ki lernt durch Millionen Spiele

Ein Eintrag (Merkmalsvekor, Datensatz) hat viele Merkmale


Hausübung
[google colab](https://colab.research.google.com/)

**It's all about features!**

# Excel Aufgabe

![[Pasted image 20260922082130.png]]

| CORREL von zwei Spalten | Abhängigkeit der Spalten |
| ----------------------- | ------------------------ |
| näher zu -1             | indirekt linear abhängig |
| näher zu 0              | unabhängig               |
| näher zu +1             | direkt linear abhängig   |
Grober richt wert: -1 bis -0,8 und 0,8 bis 1 lässt man eins der zwei features weg, um den Dimensionsraum kleiner zu machen.

![[Pasted image 20260922083448.png]]


# Wirksamkeit von Medikamenten

![[001Medikament2DDosis-Wirkung.png]]

beide Merkmale spannen jeweils eine Dimension auf. -> 2D
\+ Alter -> weitere Dimension -> 3D

Viele Dimensionen im Merkmalsraum (multidimensional)
Menge der Merkmale bestimmt nicht die Qualität des KI-Modells, sondern Merkmale müssen relevant sein (deshalb streicht man die mit Korrelation).

# Auto

![[002AutoMerkmalsvektoren.png]]

# Mathematik
$x$ ... Merkmal
$$\overline x = \frac{1}{N} \sum_{i = 1}^{N} x_i$$

$y$ ... Merkmal 2
$$\overline y = \frac{1}{N} \sum_{i = 1}^{N} y_i$$

zum selbst Implementieren, des Pearson-Korrelationskoeffizenten, $r$
$$r = \frac{ \sum_{i = 1}^{N} (x_i - \overline x) \cdot (y_i - \overline y) }{\sqrt{ \sum_{i = 1}^{N} (x_i - \overline x)^2 \cdot \sum_{i = 1}^{N} (y_i - \overline y)^2 }}$$

Wichtigste Kennzahl in der Welt der Statistik die **Varianz**

$$Var_x = \frac{1}{N} \sum_{i = 1}^{N} (x_i - \overline x)^2 $$
ergänzt um Standardabweichung $\sigma$
$$\sigma = \sqrt{Var}$$
