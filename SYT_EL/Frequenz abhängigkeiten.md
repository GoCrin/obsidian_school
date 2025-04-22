Wiederstand R -> garnicht
L -> $X_L = w * L$
w-> 0 => $X_L$ -> 0 -> KS
w -> $\infty$ => $X_L$ -> $\infty$ -> LL

C -> $X_C = \frac{1}{w * C}$
w-> $\infty$ => $X_C$ -> $\infty$ -> LL
w -> 0 => $X_C$ -> 0 -> KS

In Serienschaltung

![[Pasted image 20250422105334.png]]
Z -> Impedanz
imaginär
$X_L = j * w * L$
$X_C = \frac{1}{j * w * C}$

## Tiefpass

$H(jw) = \frac{U_a}{U_e}  = \frac{\frac{1}{j * w * C}}{R + \frac{1}{j * w * C}} * \frac{j * w * C}{j * w * C} = \frac{1}{R * w * C + 1}$
w -> 0 -> $H(jw) = 1$
w -> $\infty$ -> $H(jw)$ -> 0

Grenzfrequenz $w_g$:
Realteil = Imaginärteil
$R * w_g * C = 1$
$w_g = \frac{1}{\tau} = \frac{1}{R * C}$

$\frac{1}{j * 1 + 1} = \frac{1}{\sqrt{2} winkel 45°} = \frac{1}{\sqrt{2}} -45°$ => -3dB



$U_{R2} = R_2 * \frac{U_{ges}}{R_1 + R_2}$
