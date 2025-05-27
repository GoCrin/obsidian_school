**Viele Informationen sind noch in [[Irgendwas log]]**
## Formeln
Gain: $[G] = dB$
$$G = 20 * lg(\frac{U_{AUS}}{U_{EIN}})$$
Leistungsverhältnis: $[V_p] = 1$
$$V_p = \frac{P_{AUS}}{P_{EIN}} = 10^{\frac{G}{10}}$$
Spannungsverhältnis: $[V_u] = 1$
$$V_u = \frac{U_{AUS}}{U_{EIN}} = 10^{\frac{G}{20}}$$
Ausgangspannung
$$U_{AUS} = 10^{\frac{G}{20}} * U_{EIN}$$
Attenuation $[A] = dB$
$$A = -G$$

## Bekannte Größen

| G in dB | $V_u$  | $V_u$        |
| ------- | ------ | ------------ |
| -40     | 0,0001 | 0,01         |
| -20     | 0,01   | 0,1          |
| -10     | 0,1    | $\sqrt{0,1}$ |
| -6      | 1/4    | 0,5          |
| -3      | 1/2    | $1/\sqrt{2}$ |
| 0       | 1      | 1            |
| 3       | ~2     | $\sqrt{2}$   |
| 6       | ~4     | ~2           |
| 10      | 10     | $\sqrt{10}$  |
| 20      | 100    | 10           |
| 40      | 10.000 | 100          |

## Relative Pegel

Sind ein Verhältnis von 2 Größen, meist Ausgans- zu Eingangsgrößen (z.B. $\frac{U_{AUS}}{U_{EIN}}$)
## Absolute Pegel

diese Pegel setzen Größen in Verhältnis zu absoluten (fixen) Werten. In den meisten Fällen ist die Einheit eines solchen Pegels: `dB<fixer Wert>`, heißt, dass das Verhältnis bei z.B. $db\mu V$ gleich $\frac{U_{AUS}}{1\mu V}$ ist.

| Bezeichnung | $X_{EIN}$          | Beschreibung |
| ----------- | ------------------ | ------------ |
| $dbV$       | $U_{EIN} = 1V$     |              |
| $dbmV$      | $U_{EIN} = 1mV$    |              |
| $db\mu V$   | $U_{EIN} = 1\mu V$ |              |
