log(10) = 1

log(10^2) = 2
log(10^3) = 3


![[Pasted image 20250401104413.png]]
$$x * x = x^2 = 10$$
$$x = \sqrt{10}$$

Diese mal 2 kommen von $\sqrt[3]{10} \tilde= 2$ (dritte Wurzel 10)

Was ist dezi?
	x10

$10 * lg{P_2} / {P_1} * (U^2_2 / R) / (U^2_1 /R) = 10 * lg(U^2_2 * R) / (U^2_1 * R) = 20 * lg(U_2/U_1)$ 

$P = U^2 / R$ 
An einem Widerstand hängen P und U, quadratisch zusammen

$P_2 / P_1 = 10^{G/10}$
$V_u = 10^{G/20}$

G = 20 * lg(U2/U1)

G/20 = lg(U2/U1)

10^(G/20) = U2/U1



$U_2 / U_1 = $

| G in dB | $V_p = P_2 / P_1$ | $V_u = 1$    |
| ------- | ----------------- | ------------ |
| -40     | 0,0001            | 0,01         |
| -20     | 0,01              | 0,1          |
| -10     | 0,1               | $\sqrt{0,1}$ |
| -6      | 1/4               | 0,5          |
| -3      | 1/2               | $1/\sqrt{2}$ |
| 0       | 1                 | 1            |
| 3       | ~2                | $\sqrt{2}$   |
| 6       | ~4                | ~2           |
| 10      | 10                | $\sqrt{10}$  |
| 20      | 100               | 10           |
| 40      | 10.000            | 100          |
	
## 3. Relative Pegel

$G_1 = 20dB G_2 = -100dB G_3 = 80dB$

## 4. Absolute Pegel

### $dB\mu$

$$L_{U/V_\mu} = 20 * lg(\frac{U}{1 \mu V}) dB (\mu V)$$

### dBV

$$L = 20 * lg(\frac{U}{1V}) dBV$$

L/20 = lg(U/1V)
	u = 10^L/20 * 1V

Clipping: Signal ist lauter als obergrenze (digital)

## Beispiele

### 1.

![[Pasted image 20250408105125.png]]
* $G_3 = 40dB$
* $L_{12} = 33dBm$ (m für Leistungspegel -> milli watt)
* $L_{23} = -43dBm$
* $L_{1E} = 0dBm$
**Gesucht:** $G_1; G_2; L_{3A}$

$G_1 = L_{12} - L_{1E} = 33dBm - 0dBm = 33dB$
$mW : mW = 1$ (vor logarithmieren war Subtraktion, Division -> mW fällt weg)

$G_2 = L_{23} - L_{12} = -43dBm - 33dBm = -76dB$

$L_{3A} = G_3 + L_{23} = 40dB + (-43dBm) = -3dBm$
$1 * mW = mW$

### Boxen haben relative Pegel & Verbindungen haben absolute Pegel

### 2.
**A= 6dB / Abstandsverdoppelung**
Nach 10m -> $80dB_{SPL}$ 
Nach 20m -> $74dB_{SPL}$

$Abstand * 2$ und $-6dB$

### 3.
**Angabe:**
Auf einer großen Freifläche soll im Abstand von 100m vom Lautsprecher ein Schalldruckpegel von 76dB SPL erreicht werden.
Berechnen Sie in welchem Abstand zum Lautsprecher die 100dB-Grenze überschritten wird.

100m -> $76dB_{SPL}$
?m -> $100dB_{SPL}$

$100dB_{SPL} - 76dB_{SPL} = 24dB_{SPL}$

24 / 6 = 4
-> 4 mal halbieren
$100m / 2^4 = 6.25$

