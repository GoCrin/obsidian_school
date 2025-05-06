Wiederstand R -> garnicht
L -> $X_L = w * L$
w-> 0 => $X_L$ -> 0 -> KS
w -> $\infty$ => $X_L$ -> $\infty$ -> LL

C -> $X_C = \frac{1}{w * C}$
w-> $\infty$ => $X_C$ -> 0 -> KS
w -> 0 => $X_C$ -> $\infty$ -> LL

In Serienschaltung

![[Pasted image 20250422105334.png]]
Z -> Impedanz
imaginär
$X_L = j * w * L$
$X_C = \frac{1}{j * w * C}$

## Tiefpass (eng. Highcut)

$H(jw) = \frac{U_a}{U_e}  = \frac{\frac{1}{j * w * C}}{R + \frac{1}{j * w * C}} * \frac{j * w * C}{j * w * C} = \frac{1}{1 + R * w * C}$
w -> 0 -> $H(jw) = 1$
w -> $\infty$ -> $H(jw)$ -> 0

Grenzfrequenz $w_g$:
Realteil = Imaginärteil
$R * w_g * C = 1$

### $\omega_g = \frac{1}{\tau}$
$w_g = \frac{1}{\tau} = \frac{1}{R * C}$

$\frac{1}{j * 1 + 1} = \frac{1}{\sqrt{2} winkel 45°} = \frac{1}{\sqrt{2}} -45°$ => -3dB

$U_{R2} = R_2 * \frac{U_{ges}}{R_1 + R_2}$

**Diagramm einfügen**

Dekade (\*10)
Abfall von 20dB pro Dekade

-6dB pro Oktave (\*2)

### Normierte Form
$H(jw) = \frac{1}{1 + \frac{w}{w_g}} = \frac{1}{1+ j * \frac{f}{f_g}}$
$|H(j\omega)| = \frac{1}{\sqrt{1 + (\frac{f}{f_g})^2}}$
$|H(j\omega)|_{dB} = 20 * lg(\frac{1}{\sqrt{1 + (\frac{f}{f_g})^2}})dB$
Immer wenn es um Spannungsverhältnis geht -> 20 (nicht 10)

arg $H(j\omega) = 0° - arctan(\frac{f}{f_g})$

## Hochpass (Lowcut)
hohe Frequenz -> geht durch
tiefe Frequenz -> wird weg geschnitten

**Diagramm einfügen**

Steigung von 20dB pro Dekade
+6dB pro Oktave (\*2)

# RL-Filter
$X_L = \omega * L$
$\omega_g = \frac{1}{\tau}$
$\tau = \frac{L}{R}$
## Tiefpass

**skizze einfügen**

$\omega$ -> 0: $X_L$ -> 0 => $U_a = U_e$
$\omega$ -> $\infty$: $X_L$ -> $\infty$ => $U_a = 0V$

**diagramm einfügen**

0dB -> grenzfrequenz  ($f_g$) -> -20dB/Dekade oder -6dB/Oktave
## Hochpass

**skizze einfügen**

$\omega$ -> 0: $X_L$ -> 0 => $U_a = 0V$
$\omega$ -> $\infty$: $X_L$ -> $\infty$ => $U_a = U_e$

**diagramm einfügen**

20dB/Dekade oder 6dB/Oktave -> 0dB -> grenzfrequenz  ($f_g$)

