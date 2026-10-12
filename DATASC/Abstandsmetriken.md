Einsatz der Algorithmen: **K-Means**, **DBScan** & **K-Nearest-Neighbor**

## Abstände & Distanzen
Merkmale / Features spannen einen Raum auf. Zur besseren Vorstellung 2D/3D

Punkte im raum → (bedeuten) Abstände messen

auch Wörter werden in einen Vektor umgerechnet z.B. Word2Vec ein Model für die Verarbeitung von Sprache

"König" + "Sohn" => "Prinz" + "Mädchen" => "Prinzessin"

## Distanzmetrik

![[Pasted image 20261006084702.png]]

$$dist_{Euklid} = \sqrt{\Delta x^2 + \Delta y^2}$$
$$dist_{Manhattan} = \Delta x + \Delta y$$
Cosinus-Ähnlichkeit (Cosine-Similarity)
$$sim_{cos} = cos(\theta) = \frac{a \cdot b}{||a|| \cdot ||b||} = \frac{a_x \cdot b_x + a_y \cdot b_y}{\sqrt{a_x^2 + a_y^2} \cdot \sqrt{b_x^2 + b_y^2}}$$
$||x||$ … euklidischer Abstand zum Nullpunkt

$sim_{cos} \uparrow$ ... sehr ähnlich (Fernrohr wenig bewegen!)
$sim_{cos} \downarrow$ ... unähnlich

Praxiseinsatz von $sim_{cos}$ bei Bag-of-Ward-Verfahren, ob zwei Vektoren (unabhängig von ihrer Länge) in die gleiche Richtung zeigen

![[Pasted image 20261006090431.png|198]]

"Heute scheint die Sonne."
"Heute schein die Sonne besonders stark."

Das Ganze geht mit sehr vielen Dimensionen (n Dimensionen)

Hinweis zu Cosinus-Distanz:
$$dist_{cos}(a,b) = 1 - sin_{cos}(a,b)$$