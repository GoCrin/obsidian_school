# 1. Hausübung am 15. September 2025
## 1) Paradoxon von Zenon (Achilles und die Schildkröte)
Berechne nach welcher Strecke Achilles die Schildkröte einholen wird, wenn die Schildkröte mit 30m Vorsprung startet und Achilles 4 mal so schnell wie die Schildkröte läuft.

geg:
* $v_a = 4 v_s$
* $s_a = v_a * t$
* $s_s = v_s * t + 30$
* $s_a = s_s$ am Treffpunkt

ges:
* zurückgelegte Meter bis zum Treffpunkt

$$s_a = s_s$$
$$ v_a * t = v_s * t + 30 $$
$$ 4 v_s * t = v_s * t + 30 $$
$$ 4 v_s * t = v_s * t + 30 $$
$$ 4 v_s * t - v_s * t = + 30 $$
$$ t * (4 v_s - v_s) = 30 $$
$$ 3 v_s * t = 30 $$
$$ t = 10 / v_s $$
$$ s_a = v_a * \frac{ 10 }{ v_s } $$
$$ s_a = v_a * \frac{ 10 }{ \frac{ v_a }{ 4 } } $$
$$ s_a = v_a * \frac{ 40 }{ v_a } $$
$$ s_a = 40 $$

A: Achilles holt die Schildkröte nach 40 Metern ein.

## 2)
Die elektrische Stromstärke $i(t)$ bei einem Wechselstromverbraucher kann durch eine Sinusfunktion beschrieben werden: $i(t) = 2 sin(10t + 30°)$, $t$…. Zeit in sec,$i(t)$ …. Stromstärke zur Zeit $t$ in A. Berechne die zeitliche Änderungsrate des Stromes für t = 5 s!

$$ i'(t) = 20 cos(10t + 30°) $$

$$ i'(5s) = 20 cos(80) $$
$$ i'(5s) = -2.21 A $$


## 3)
geg:
* $f(x) = a * x^2 + b * x$
* $P = (200|0)$
* $f'(0) = \frac{1}{10}$


ges:
* a, b
* Achsen bei funktion $g(x) = a * x^2$

### 3.1)

$$ f'(x) = 2ax + b $$

Gleichungssystem:
$$ 0 = 40000a + 200b $$
$$ b = \frac{1}{10} $$
$$ a = - \frac{1}{2000} $$

### 3.2)

![[15092025_coords.png]]

# 2. Hausübung am 17 September 2025

4.59)

ges
* $f_1$
* $f_1$

$$ f_1'(0)= 0 $$
$$ f_1'(0,5)= 0,5 $$
$$ f_1(0)= 1 $$

$$b = 0 $$
$$c = 1 $$
$$0,5 = a (0,5)^2 + 0,5b + c $$
$$0,5 = a 0,25 + 1 $$
$$a = -2 $$
$$f_1(x) = -2x^2 + 1 $$

$$ f_2'(1)= 0 $$
$$ f_2'(0,5)= 0,5 $$
$$ f_2(1)= 0 $$

$$ 0 = 2a + b $$
$$ 0,5 = (0,5)^2 a + 0,5 b + c $$
$$ 0 = a + b + c $$

$a = 2$, $b = -4$, $c = 2$


$$ f_2(x) = 2 x^2 -4 x + 2 $$

bigskip
bigskip

## 1)

geg: $\int \frac{\frac{3}{7} sin x}{2} \,dx$

$$ \frac{3}{14} \int sin x \,dx $$
$$ - \frac{3}{14} cos x + c $$

## 2)

geg: $\int \frac{2 - t}{t^2} \,dt$

Verwendet wird dieser "Trick": $\int u * v' = u * v - \int u' * v$

$$ (2 - t) * (- \frac{1}{t}) - \int t^{-1} \,dt $$
$$ - \frac{2}{t} - ln|t| + c $$

## 3)

geg: $\int (\frac{x}{2} - 2)^2 \,dx$

$$ \int \frac{x^2}{4} - 4 \frac{x}{2} + 4 \,dx $$
$$ \frac{1}{4} \int x^2 - 2 \int x \,dx + 4 $$
$$ \frac{1}{12} x^3 - x^2 + c $$

## 4)

geg: $\int ( 2a - x )^2 \,dx$

$$ 4a^2 - 4a \int x + \int x^2 \,dx $$
$$ \frac{1}{3} x^3 - 2ax^2 + c $$

## 5)

geg: $\int \frac{a - 2}{b^2 + c * t} \,dt$

$$ (a - 2) \int (b^2 + c * t)^{-1} \,dt $$

Einsatz von "Trick": Integration durch Substitution

$u = b^2 + c * t$ -> $\frac{du}{dt} = c$ -> $dt = \frac{du}{c}$

$$ (a - 2) \int u^{-1} \frac{1}{c} \,du $$
$$ \frac{1}{c} (a - 2) ln|u| + c $$
$$ \frac{1}{c} (a - 2) ln|b^2 + c * t| + c $$

## 6)

geg: $\int 2 x^2 * \sqrt[5]{x^3 - 1} \,dx$

$u = x^3 - 1$ -> $\frac{du}{dx} = 3 x^2$ -> $dx = - \frac{du}{3 x^2}$

$$ 2 \int x^2 u^{1/5} \frac{1}{3 x^2} \,du $$
$$ \frac{2}{3} \int u^{1/5} \,du $$
$$ \frac{2}{3} \frac{u^{6/5}}{\frac{6}{5}} + c $$
$$ \frac{10}{18} (x^3 - 1)^{\frac{6}{5}} + c $$

## 7)

geg: $\int 3 - 2e^{k * t} \,dt$

$u = -kt$

$$ 3 - 2 \int e^u (-\frac{1}{k}) \,du  $$
$$ 3 + \frac{2}{k} e^u + c $$
$$ \frac{2}{k} e^{-kt} + c $$

## 8)

geg: $\int 2 sin(2x) * e^{cos(2x)} \,dx$

$u = cos(2x)$ -> $\frac{du}{dx} = -2 sin(2x)$ -> $dx = - \frac{du}{2 sin(2x)}$

$$ 2 \int e^u * sin(2x) * \frac{1}{2 sin(2x)} \,du $$
$$ \int e^u \,du $$
$$ e^u + c $$
$$ e^{cos(2x)} + c $$
# 3. Hausübung, am 25.9.2025

## 1)

geg:
$\int x^{-4} * x^3 \,dx$

$$ \int x^{-1} \,dx $$
$$ ln|x| + c $$

## 2)

geg:
$\int 3 \,dt$

$$ 3 + c $$


## 3)

geg:
$\int u * \sqrt{u} \,du$

$$ \frac{2}{5} * \sqrt{u^5} + c $$

## 4)

geg:
$\int \sqrt{\frac{1}{x}} \,dx$


$$ 2 \sqrt{x} + c $$


## 5)

geg:
$\int \frac{1}{cos^2t} \,dt$


Ich weiß nicht wie man das berechnet. Lösung laut Geogebra:

$$ tan(x) + c $$

## 6)

geg:

$\int \,dx$

$$ 1 + c $$

## 7)

geg:
$\int t * e^{-s * t} \,dt$

$$ t * ( - \frac{1}{s}) * e^{-st} - \int - \frac{1}{s} * e^{-st} \,dt $$
$$ - \frac{t}{s} * e^{-st} - \frac{1}{s} * e^{-st} + c $$
$$ - \frac{1}{s} * e^{-st} * (t + 1) + c $$

## 8)

geg:
$\sqrt{1 - s} \,ds$

$$ -1 \int (u)^{\frac{1}{2}} \,du $$
$$ -1 * \frac{u^{\frac{3}{2}}}{\frac{3}{2}} + c $$
$$ - \frac{3}{2} \sqrt{u^3} + c $$
$$ - \frac{3}{2} \sqrt{(1 - s)^3} + c $$
# 4. Hausübung am 6.10.2025

## 1)

geg:
$\int \frac{x^2 - x + 1}{2x} \,dx$



$$ \frac{1}{2}  \int \frac{x^2 - x + 1}{x} \,dx $$
$$ \frac{1}{2}  \int (x^2 - x + 1) * x^{-1} \,dx $$
$$ \frac{1}{2} * (\int \frac{x^2}{x} \,dx - \int \frac{x}{x} \,dx + \int \frac{1}{x} \,dx) $$
$$ \frac{1}{2} * (\frac{1}{2} * x^2 + ln|x|) + c $$
## 2)

geg:
$\int t * e^{-s*t} \,dt$


$$ t * (- \frac{1}{s}) * e^{-s*t} - \int 1 * (- \frac{1}{s}) * e^{-s*t} \,dt $$
$$ - \frac{t}{s} * e^{-s*t} - \frac{1}{s^2} * e^{-s*t} + c$$
$$ - \frac{1}{s} * e^{-s*t} * (t + \frac{1}{s}) + c $$



## 3)

geg:
$\int e^{-x+2} \,du$



$$ x + c $$



## 4)

geg:
$\int \frac{2 * e^x}{1 + e^x} \,dx$



$$ 2 * \int e^x * \frac{1}{e^x} * u^{-1} \,du $$
$$ 2 * ln|u| + c $$
$$ 2 * ln|1 + e^x| + c $$



## 5)

geg:
$\int (3 + 2x)^4 \,dx$



$$ \frac{1}{2} * \int u^4 \,du $$
$$ \frac{1}{10} * u^5 +c $$
$$ \frac{1}{10} * (3 + 2x)^5 + c $$

# 5. Hausübung, am 8.10.2025



## 1)
geg:
\(\int \frac{x * (2 - x^3)}{\sqrt[4]{(5x^5 - 25x^2 + 9)^3}} \,dx\)



$$\int \frac{x * (2 - x^3)}{25x^4 - 50x} * \frac{1}{\sqrt[4]{u^3}} \,du $$
$$\int \frac{(2 - x^3)}{25 * (x^3 - 2x) * (-1) * (-1)} * \frac{1}{\sqrt[4]{u^3}} \,du $$
$$ - \frac{1}{25} * \int u^{- \frac{3}{4}} \,du $$
$$ - \frac{1}{25} * 4 * u^{\frac{1}{4}} + c $$
$$ - \frac{4}{25} * \sqrt[4]{5x^5 - 25x^2 + 9} $$



## 2)
geg:
$\int \frac{4 \,dx}{\sqrt[3]{ax + b}} \,dx$



Substitution nicht weiter verfolgbar da x nicht wegfällt (Angabe Fehler?)



## 3)
geg:
$\int sin^2(x) * cos(x) \,dx$



$$ \int u^2 \,du $$
$$ \frac{1}{3} * sin^3(x) + c $$



## 4)
geg:
$\int e^x sin^2 x \,dx$



Verwendung von mir Unbekannten Integrationsformeln

$$\int e^{x}\sin^{2}(x)\,dx = \frac{e^{x}}{10},\bigl(5 - \cos(2x) - 2\sin(2x)\bigr) + c$$

# 6. Hausübung, am 14.10.2025



## 1)
geg:
\(\int ln(x) \,dx\)



$$ x * ln(x) - x + c $$



## 6.8)a

\(f(x) = 0,5 * x + 2\), davon Ober- und Untersumme im Integral a=0 bis b=2, mit n=4



Untersumme:

$$ \sum_{i = 0}^{n - 1} f(i) * \Delta x = 5,5 $$

Obersumme:

$$ \sum_{i = 1}^{n} f(i) * \Delta x = 6,5 $$

Beide scheinen Flasch, da das Bestimmte Integral 5 ist.



## 6.24)b
geg:
$\int_{-1}^{1} 2 + e^x \,dx$



$$F(a) = F(-1) = -1,63 $$
$$F(b) = F(1) = 4,72$$
$$F(b) - F(a) = 6,35$$

# 7. Hausübung, am 21.10.2025
## 7.61
### a)
Der Inhalt der markierten Fläche in dem Diagramm zeigt die zurückgelegte Distanz des PKWs. 
### b)
**geometrisch**
$$A = A_R + A_T$$
$$A_R = 2 * 20 = 40$$
$$A_T = \frac{2 * 10}{2} = 10$$
$$A = 40 + 10 = 50m$$
**durch Integration**
$$\int_0^2 5 t + 20 \,dt$$
$$F(x) = \frac{5}{2} t^2 + 20t$$
$$F(0) = 0$$
$$F(2) = 50$$
$$\int_0^2 5 t + 20 \,dt = F(2) - F(0) = 50$$
## 7.62
### a)
Die Geschwindigkeit des Steins nimmt ab bis er seinen Höhepunkt erreicht, wo $v = 0 m/s$. Danach nimmt die Geschwindigkeit wieder zu nur in Richtung Boden, was im Graph durch eine negative Geschwindigkeit dargestellt wird.
### b)
$$\int_0^{0,5} v(t) \,dt = \int_0^{0,5} -10  t + 15 \,dt $$
$$F(x) = -5 t^2 + 15 t$$
$$\int_0^{0,5} v(t) \,dt = F(0,5) = 6,25$$
$$\int_0^{1} v(t) \,dt = F(1) = 10$$
Diese Flächen zeigen wie viele Meter der Stein in der Luft ist und wie dieser nach oben fliegt.
### c)
$$A_{0,5} = \frac{5 * 0,5}{2} + 10 * 0,5 = 6.25$$
$$A_1 = \frac{10 * 1}{2} + 5 * 1 = 10$$
## 7.63
### a)
$20m$
### b)
$40m$

## 7.64
Die anfängliche Absprunghöhe kann durch das Berechnen der gesamten Fläche unter der Kurve ermittelt werden, da diese Zeigt wie weit der Fallschirmspringer oder die Fallschirmspringerin gefallen ist bis er oder sie am Boden am kam.
## 7.70
Sie ist negativ und nimmt ab.

## SRDP 032

### 1)
$$f'(x) = \frac{6}{100} * x^3$$
$$\frac{15}{1000} * x^4 - 3 = 0$$
NS durch Geogebra
![[Pasted image 20251103183250.png]]
$$x = 3,76$$
$$f'(3,76) = 3,19$$
$$\beta = arctan(3,19) = 72,59°$$
$$\alpha = 180° - \beta = 107,4°$$
### 2)
![[Pasted image 20251103184925.png]]
$A = 18,05$

Es fließen $21,66 m^3 / s$

# 8. Hausübung, am 18.11.2025
## 7.29
$$V = \pi \int_a^b x^2 \,dx$$
## 7.36
$$y = 1 - x^2 -> x = \sqrt{y - 1}$$
## 7.34
$$f(x) = \frac{1}{40}x^2 - \frac{1}{20} x + 3$$
$$V_{12} = \pi \int_0^{12} f(x)^2 \,dx = 604,39 ml$$
$$500ml = \pi \int_0^b f(x)^2 \,dx = 10,99$$
## 7.44

![[Pasted image 20251124194450.png]]
## 7.49
![[Pasted image 20251124194624.png]]

# 9. Hausübung, am 26.11.2025

## SRDP B_578 c)

1:
* $a = 9,5$
* $d = 10$

2:
* $b = \frac{\pi}{15}$
* $c = 0$

3:
* $100,34$
## SRDP B_567 
### a)
1: 1\. Maxima bei $P(10|1)$

2: Die Länge der Makierungslinie bis 30 Meter

3: $- \frac{\pi}{2}$
### b) 

1: $4,98s$
2: $199,6$
3: Dies ist die zurückgelegte Distanz des Autos in Metern in den ersten 10 Sekunden

# 10. Hausübung, am 8.12.2025
## 3.8
1. wahr
2. falsch
3. wahr
4. wahr
5. wahr

## 1

$2 = (2x)^2$ f.A.
$cos(x) = (sin(x))^2$ f.A.
$e^x = e^{x2}$ f.A.
Daher muss e) richtig sein.

## 3.10 b)
$y' + x + 2 = 0$
$y = -\frac{1}{2}x^2 - 2 x + C$

## 3.12 b)
$y' + x^2 = x + 1$; $y(6) = 0$
$y = -\frac{1}{3}x^3 + \frac{1}{2}x^2 + x + 6$

# 11. Hausübung, am 10.12.2025
## 3.16
### a)
$$h'(t) = -gt + C_1$$
### b)
$v_0 = 20m/s$ ... Anfangsgeschwindigkeit
$H = 2m$ ... Wurfhöhe
$$h(t) = - \frac{g}{2}t^2 + C_1 t + C_2$$
$$h(t) = - \frac{g}{2}t^2 + v_0 t + H$$
### c)
![[Pasted image 20251210190536.png]]
Punkt C aus GeoGebra: Nach 2 Sekunden erreicht der Ball seine höchste Flughöhe.
### d)
Punkt B aus GeoGebra: Nach 4.1 Sekunden landet der Ball am Boden.
## 3.17
### a)
$$s'(t) = -8t + \frac{90}{3,6}$$
$$s(t) = -4t^2 + 25t + C$$
### b)
Als $C$ die Distanz die der Fahrer in der Schrecksekunde fährt
$$s(t) = -4t^2 + 25t + 25$$
### c)
![[Pasted image 20251210192403.png]]
Da durch der Punkt mit der Steigung 0 bei y 64,06 liegt und dieser der ist bei dem das Auto steht. Trifft der Fahrer das Reh nicht.
## 3.18 a)
$$y' = x^2 - x + C_1$$
$$y = \frac{1}{3}x^3 - \frac{1}{2}x^2 + C_1 x + C_2$$
$y(0) = 1$ -> $C_2 = 1$
![[Pasted image 20251210194344.png]]
$$C_1 = -9$$

# 12. Hausübung, am 7.1.2026
## 3.21
### a)
$$y(L)=0$$
$$y'(L)=0$$
### b)
$$y''(x) = \frac{F}{E*I} x$$
$$y'(x) = \frac{F}{2 * E * I} x^2 + C_1$$
$$y(x) = \frac{F}{6 * E * I} x^3 + C_1 * x + C_2$$
Konstanten:
$$0 = \frac{F}{2 * E * I} L^2 + C_1$$
$$C_1 = - \frac{F L^2}{2 E I}$$
$$0 = \frac{F}{6 * E * I} L^3 - \frac{F}{2 * E * I} L^3 + C_2$$
$$C_2 =\frac{F * L^3}{E * I} * (\frac{1}{2} - \frac{1}{6})$$
$$C_2 = \frac{ F L^3}{3 E I}$$
Lösung:
$$y(x) = \frac{F}{6 E I} x^3 - \frac{F L^2}{2 E I}  x + \frac{ F L^3}{3 E I}$$
$$y(x) = \frac{F}{6 E I} (x^3 - 3 L^2 x + 2 L^3)$$
### c)
$$y(0) = \frac{L^3 F}{3 E I} = \frac{64m^3 * 10kN}{24 * 10^6 Nm^2} = 0,02\dot6 m$$
### d)
Bei einer Verdoppelung von $L$ ist die Lösung für $y(0)$ gleich $0,21\dot3$, was einer Verachtfachung entspricht
# 13. Hausübung, am 19. 1. 2026
## 3.30 a)
![[Pasted image 20260119195847.png]]
## 3.31 a)
$y' = y -4$ mit $y(0) = 1$
$$\frac{dy}{dx} = 1 * (y-4)$$
$$\int\frac{1}{y - 4} \,dy = \int 1\,dx$$
$$ln|y-4| + c_1 = x + c_2$$
$$y-4 = e^x * c$$
$$y = e^x * c + 4$$
$$1 = e^0 * c + 4$$
$$-3 = c$$
$$y = -3 e^x + 4$$
## 3.31 b)
$y' = -x * y$ mit $y(0) = 1$
$$\int \frac{1}{y} \,dy = - \int x \,dx$$
$$ln|y| + c_1 = -\frac{1}{2}x^2 + c_2$$
$$ln|y| = \frac{1}{2}x^2 + c$$
$$y = e^{\frac{1}{2}x^2} * c$$
$$c = 1$$
$$y = e^{\frac{1}{2}x^2}$$

## 3.32 f)
$y' * cos\,x + y * sin\,x = 0$
$$y' = - y * tan\,x$$
$$\frac{dy}{dx} = -y * tan\,x$$
$$- \frac{1}{y}\,dy = tan\,x\,dx$$
$$-ln|y| = -ln|cos(x)| + c$$
$$y = cos(x) + c$$

## 3.33 b)
$y' + y = 1$; $y(0) = 3$
$$- ln|1-y| = x + c$$
$$y =1 - e^{-x} * c$$
$$3 = 1 - c$$
$$c = -2$$
$$y = 1 + 2 e^{-x}$$

# 14. Hausübung, am 8. 2. 2026
## 3.36
### a)
Die Änderungsrate ist negativ, da Zerfall eine Minderung der Anzahl zu Folge hat.
### b)
$$\int\frac{1}{N}\,dN = - \lambda \int \,dt$$
$$ln|N| = -\lambda * t + c_1$$
$$N(t) = e^{-\lambda t}*c$$
$$N(0) = N_0 = e^{-\lambda t}*c$$
$$c = \frac{N_0}{e^0} = N_0$$
$$N(t) =N_0 * e^{-\lambda t}$$
## 3.38
### a)
Weil der Luftdruck mit steigender höhe geringer wird.
### b)
$$\int \frac{1}{p} \,dp=-k \int \,dh$$
$$ln|p| = -k * h + c_1$$
$$p(h) = e^{-k h} * c$$
$$p(0) = 1013hPa = e^{-k h} * c$$
$$c = 1013hPa$$
$$p(h) =1013 * e^{-k h}$$
### c)
$$\frac{p(h_{1/2})}{p_0} = \frac{1}{2} = e^{-k*h_{1/2}}$$
$$h_{1/2} = \frac{ln(2)}{k} = 5,54km$$
### d)
$$0,4 = e^{-k * h}$$
$$h = \frac{ln(\frac{5}{2})}{k} = 7,32km$$
### e)


| Höhe      | International | Barometrisch |
| --------- | ------------- | ------------ |
| $h=3km$   | $701hPa$      | $695hPa$     |
| $h = 8km$ | $356hPa$      | $372hPa$     |

## 3.41
### a)

$$V = \pi R^2 h$$
$$\frac{\pi R^2 dh}{dt} = -\mu A_0 \sqrt{2g*h(t)}$$
$$\int \frac{1}{\sqrt{h}}\,dh=-\frac{\mu r^2 \sqrt{2g}}{R^2} \int\,dt$$
$$2\sqrt{h} = -\frac{\mu r^2 \sqrt{2g}}{R^2} * t + c_1$$
$$h_a(t) = (-\frac{2\mu r^2 \sqrt{2g}}{R^2} * t + c)^2$$
$$h(0) = H = c^2$$
$$c = \sqrt{2}$$
$$h_s(t) = (\sqrt{2} -\frac{2\mu r^2 \sqrt{2g}}{R^2} * t)^2$$
![[Pasted image 20260210193235.png]]
### b)
![[Pasted image 20260210193531.png]]
### c)
![[Pasted image 20260210193651.png]]
## 3.42
### a)

$$\frac{dv}{dt} = -g  -\frac{k}{m}v^2$$
$$\int\frac{1}{g+\frac{k}{m}v^2}\,dv = -\int\,dt$$
Geogebra:
![[Pasted image 20260211075657.png]]
$$2m*\frac{tan^{-1}(k*\frac{v}{\sqrt{gkm}})}{2*\sqrt{gmk}} = -t + c_2$$
![[Pasted image 20260211080854.png]]
$$v(t)_a = -30 * tan(\frac{c}{3}+\frac{t}{3})$$
$$30 = -30 * tan(\frac{c}{3})$$
$$-1 = tan(\frac{c}{3})$$
$$c = \frac{3 \pi}{4}$$
$$v(t)_s = -30 * tan(\frac{\pi}{4}+\frac{t}{3})$$
Irgendwo ist ein Fehler passiert. Lösung ist gespiegelt:
$$v(t)_s = 30 * tan(\frac{\pi}{4}-\frac{t}{3})$$
### b)
$$v(t_{max}) = 0$$
$$30*tan(\frac{\pi}{4} -\frac{t}{3}) = 0$$
$$t_{max} = \frac{3 \pi}{4} = 2.36s$$

### c)
![[Pasted image 20260210202641.png]]


## SRDP B_674 c
### 1
1. A
2. C

### 2
$$\frac{8,2 - 10}{70 - 25} = -0,04kW/°C$$
## SRDP B_627 c
$$\dot{u}(t) = k * (U_0 - u)$$

## SRDP B_566 d
### 1
$$\dot{f}(t) = k * (G - f)$$
### 2
$$f(0) = 1000 - 900*e^{-k*0} = 1002$$
### 3
Da $e^{-kt}$ für $t$ -> $\infty$ gegen $0$ geht, geht der rechte Term verloren und es bleibt der linke Term: $1000$.

# 15. Hausübung am 15. 2. 2025

## 3.10 f

$$\frac{dy'}{x} = 4 x - 12 x^2$$
$$y' + c_1 = 2x^2 - 4 x^3 + c_2$$
![[Pasted image 20260216180935.png]]
$$y = \int 2x^2 - 4x^3 + c_3 \,dx$$
$$y(x)_a = \frac{2}{3} x^3 - x^4 + c_3 x + c_4$$
## 3.12 d

$$y' = \int 1- x - 6x^2 \,dx$$
![[Pasted image 20260216181332.png]]
$$y' = -2x^3 - \frac{1}{2} x^2 + x + c_1$$
$$y(x)_a = - \frac{1}{2} x^4 - \frac{1}{6} x^3 + \frac{1}{2} x^2 + c_1 x + c_2$$
$$2 = c_2$$
$$5 = c_1$$
$$y(x)_a = - \frac{1}{2} x^4 - \frac{1}{6} x^3 + \frac{1}{2} x^2 + 5 x + 2$$

## 3.32 d

$$\frac{dy}{dx} = -x * y^2$$
$$\int \frac{1}{y^2} \,dy =- \int x \,dx$$
$$- \frac{1}{y} + c_1 = \frac{1}{2} x^2 + c_2$$
$$y = - \frac{1}{\frac{1}{2} x^2 + c_3}$$

## 1)

$$f'(x) = \frac{1}{x}$$
$$P = (1; 2)$$
$$f(x) = ln|x| + c$$
$$2 = ln(1) + c$$
$$c = 2$$
$$f(x) = ln|x| + 2$$

##  2)
### a & b)
$$s''(t) = - 4$$
$$s'(t) = v(t) = -4t + 20$$
$$s(t) = -2t^2 + c_1 t + c_2$$
$$s(t) = -2t^2 + 20 t$$
### c)
$$v(t) = 0 = -4t + 20$$
$$t = 5s$$

$$s(5) = 50m$$

### d)
$$s(t) = 20 = -2t^2 + 20t$$
![[Pasted image 20260216184155.png]]
$$t =- \sqrt{15} + 5$$
$$v(-\sqrt{15} + 5) = 15,5$$
![[Pasted image 20260216184424.png]]

# 16. Hausübung, am 2.3.2026
## 3.52
* a: Ja
* b: Nein
* c: Nein
* d: Nein

## 3.53

A: Sie besteht aus 2 Termen, der Lösung der homogenen Gl. und eine partikuläre Lösung der inhomogenen Gl.

# 3.56)b
$$y' + x* y = 2x$$
$$\frac{dy}{dx} = -x*y$$
$$\int \frac{1}{y}\,dy = - \int x\,dx$$
$$ln|y| = -\frac{1}{2}x^2 + c_1$$
$$y = e^{-0,5x^2} * c$$
$$y = K(x) * e^{-0,5x^2}$$
$$y' = K'(x) * e^{-0,5x^2} - K(x) * x * e^{-0,5x^2}$$
$$K'(x) * e^{-0,5x^2} - K(x) * x * e^{-0,5x^2} + K(x) * e^{-0,5x^2} * x = 2x$$
$$K'(x) * e^{-0,5x^2} = 2x$$
$$K'(x) = 2xe^{0,5x^2}$$
![[Pasted image 20260309114219.png]]
$$K = 2e^{x^2/2} + C$$
$$y = (2e^{x^2/2} + C) * e^{-0,5x^2}$$
$$y = 2 + C e^{-x^2/2}$$
![[Pasted image 20260309115036.png]]

## 3.57)b
$$2x y' + y = 6x$$
$$y' = - \frac{y}{2x}$$
$$\int \frac{1}{y}\,dy = - \frac{1}{2} \int \frac{1}{x} \,dx$$
$$ln|y| = - \frac{1}{2} ln|x| + c_1$$
$$y = \frac{1}{\sqrt{x}} * c_2$$
$$y = K(x) * \frac{1}{\sqrt{x}}$$
$$y' = K'(x) * \frac{1}{\sqrt{x}} + K(x) * (-\frac{1}{2}) * \frac{1}{\sqrt{x^3}}$$
$$2x * (K'(x) * \frac{1}{\sqrt{x}} - \frac{1}{2} K(x) * \frac{1}{\sqrt{x^3}}) + K(x) * \frac{1}{\sqrt{x}} = 6x$$
$$2x K'(x) * \frac{1}{\sqrt{x}} - K(x) * \frac{1}{\sqrt{x}} + K(x) * \frac{1}{\sqrt{x}} = 6x$$
$$K'(x) = 3 * \sqrt{x}$$
$$K(x) = 2 \sqrt{x^3} + C$$
$$y = (2 \sqrt{x^3} + C) * \frac{1}{\sqrt{x}}$$
$$5 = (2 \sqrt{2^3} + C) * \frac{1}{\sqrt{2}}$$
$$C = \sqrt{2}$$
$$y = (2 \sqrt{x^3} + \sqrt{2}) * \frac{1}{\sqrt{x}}$$
# 17. Hü, am 9.3.2026
## 3.57 b
$$2xy' + y - 6x = 0; y(2) = 5$$
$$y' + \frac{1}{2x}y = 3$$
$$y' + a(x)y = b(x); a(x) = \frac{1}{2x}; b(x) = 3$$
$$y' + \frac{1}{2x}y = 0$$
$$\frac{y'}{y} = -\frac{1}{2x}$$
$$ln|y| = - \frac{1}{2}$$

# 20. Hausübung, am 13.4.2026

## 3.60) b
$$y' + 2y = e^{-2x}$$
$$y' + 2y = 0$$
$$y_h= Ce^{-2x}$$
$$y_p ​= A * x * e^{−2x}$$
$$y_p' = Ae^{−2x} − 2Axe^{−2x}$$	$$y_p' + 2y_p ​= Ae^{−2x} − 2Axe^{−2x} + 2Axe^{−2x} = Ae^{−2x} = e^{−2x}$$
$$y_p = x * e^{-2x}$$
$$y = (C + x) e^{-2x}$$
## 3.49
**Zeitkonstante:** $\tau = R \cdot C = 0{,}5,\text{s}$

**DGL:**

$$\dot{u}_C + \frac{1}{\tau},u_C = \frac{1}{\tau},u(t)$$

---

### a) $u(t) = 5,\text{V}$

$$u_C(t) = 5,\text{V} \cdot \left(1 - e^{-2t}\right)$$

> Der Kondensator lädt sich exponentiell auf $5,\text{V}$ auf. Nach $5\tau = 2{,}5,\text{s}$ ist er praktisch vollständig geladen.

---

### b) $u(t) = 4,\frac{\text{V}}{\text{s}} \cdot t$

$$u_C(t) = 4,\frac{\text{V}}{\text{s}} \cdot \left(t - 0{,}5,\text{s} + 0{,}5,\text{s} \cdot e^{-2t}\right)$$

> Der Kondensator folgt der linear ansteigenden Eingangsspannung mit einer konstanten Verzögerung von $\tau = 0{,}5,\text{s}$. Im eingeschwungenen Zustand beträgt der Spannungsversatz $a\tau = 2,\text{V}$.

---

### c) $u(t) = 26,\text{V} \cdot \sin(3,\text{s}^{-1} \cdot t)$

$$u_C(t) = 14{,}42,\text{V} \cdot \sin(3t - 56{,}3°) + 12,\text{V} \cdot e^{-2t}$$

> Die Lösung besteht aus zwei Anteilen. Der Einschwingterm $12,\text{V}\cdot e^{-2t}$ klingt mit $\tau = 0{,}5,\text{s}$ ab. Im eingeschwungenen Zustand verhält sich das RC-Glied als Tiefpass: die Amplitude wird von $26,\text{V}$ auf $14{,}42,\text{V}$ gedämpft und die Phase um $56{,}3°$ verzögert.


# 21. Hü, am 19.4.26
## 3.72 a

$$\frac{dV}{dt} = 0,04 - 0,1 * V(t)$$
### 1. Lösung Trennung der Variablen
$$\frac{1}{0,04 - 0,1 * V(t)} dV = dt$$
$$-10ln|5V(t) - 2|= t + c_1$$
$$ln|5V(t) - 2| = -0,1t + c_2$$
$$5V(t)= e^{-0,1t} * C - 2$$
### 2. Lösung Lange

$$\frac{dV}{dt} + 0,1 * V(t) = 0,04$$

**homogene Lsg**

$$\frac{dV}{dt} + 0,1 * V(t) = 0$$
$$\lambda C e^{\lambda t} = - 0,1 C e^{\lambda t}$$
$$C e^{\lambda t} * (\lambda + 0,1) = 0$$
$$\lambda = -0,1$$
$$V_h = C e^{-0,1t}$$

**Partikuläre Lsg**

$$V_p = a$$
$$0,1a = 0,04$$
$$a = 0,4$$
$$V_p = 0,4$$

**Allg Lsg**

$$V(t) = V_h(t) + V_p(t)$$
$$V(t) = C e^{-0,1t} + 0,4$$
**spezielle Lsg**

$$1,5 = C + 0,4$$
$$C = 1,1$$
$$V(t)_s = 1,1e^{-0,1t} + 0,4$$
## b

$$1 = 1,1e^{-0,1t_1} + 0,4$$
$$\frac{6}{11} = e^{-0,1t_1}$$
$$ln \frac{6}{11} = -0,1t_1$$
$$t_1 = 6,06$$

Nach 6 Minuten.

## B_603 b

### 1

$$\frac{dm}{dt} = - \lambda m$$
### 2
$$m(t) = Ce^{\beta x}$$
$$\beta C e^{\beta x} =a - \lambda Ce^{\beta x}$$
$$Ce^{\beta x} * (\beta + \lambda) = 0$$
$$\beta = - \lambda$$

### 3
$$m(0) = 1000 - 998 = 2$$
## B_049 a
$$\frac{dN}{dt} = k*N$$
$$\int \frac{1}{N} \,dN = k \int \,dt$$
$$ln|N| = k * t + c$$
$$N(t) = C e^{kt}$$
$$N(0) = 50 = C$$
$$N(100) = 750 = 50 * e^{k * 100}$$
$$k = 0,027$$
$$N(180) = 6545$$
Schneller mehr Bakterien...
## B_049 c
um die 60
$$0 < B < 1000$$

# 22. Hü, am 22.4.26

## 3.65
### a
Sie muss negativ sein, da nur so zum Zeitpunkt $t = 0$, $k * (20 - 100) = k * -80$ positiv sein kann und dieser Wert positiv sein muss, um eine Temperaturzunahme zu zeigen.

### b
Sie zeigt, dass die Temperaturänderung der Kugel proportional zu der Differenz von der aktuellen Temperatur und der Umgebungstemperatur ist.

### c
$$\frac{dT}{dt} - k * T(t) = - k * T_U$$

**homogene Lsg**

$$\frac{dT}{dt} - k * T(t) = 0$$
$$\boxed{T_h = Ce^{kt}}$$

**Partikuläre Lsg**
$$T_p = a$$
$$-k * a = -k * T_U$$
$$a = T_U$$
$$\boxed{T_p = T_U}$$

**Allgemeine Lsg**
$$T_a = T_h + T_p$$
$$\boxed{T_a = Ce^{kt} + T_U}$$

**Spezielle Lsg**
$$20 = C + T_U$$
$$C = -80$$

$$39 = -80*e^{10k} + 100$$
$$\frac{61}{80} = e^{10k}$$
$$k = \frac{ln(\frac{61}{80})}{10} = -0,02712$$
$$\boxed{ T(t) = -80 * e^{-0,027t} + 100 }$$

### d
$$\boxed{ T(20) = -80 * e^{-0,027 * 20} + 100\ \tilde=\ 53,5°C}$$

### e
$$\boxed{t = \frac{ln(\frac{1}{8})}{-0,027}\ \tilde{=}\ 76,69s = 1'17''}$$

### f
Ja es ist ein beschränkter Wachstumsvorgang (der sich 100° asymptotisch annähert)? Ich **verstehe** die Aufgabenstellung **nicht**.

## B_661 b
### 1)
$$\frac{dm}{dt} = a - k * m$$
$$\int\frac{1}{a-k*m}\,dm = \int\,dt$$
$$-\frac{ln|k*m - a|}{k} = t + c_1$$
$$ln|k*m - a| = -k*t + c_2$$
$$k*m-a = e^{-k*t}*c_3$$
$$m = \frac{e^{-k*t}*c_3 + a}{k}$$

### 2)
$$m(t) = \frac{a}{k} * (1- e^{-k*t})$$
$$m'(t) = a*e^{-k*t}$$
$$a*e^{-k*t} = a - k * \frac{a}{k} * (1- e^{-k*t})$$
$$e^{-k*t} = 1 - 1 + e^{-k * t}$$
$$0 = 0$$

### 3)
Durchschnittliche Masseänderung in $mg$ zwischen zwei Zeitpunkten.

## B_487 a

### 1)
$$\boxed{\frac{dE}{dx} = -k E}$$

### 2)
$$\int \frac{1}{E} \,dE = -k \int \,dx$$
$$ln|E| = -kx+c_1$$
$$\boxed{E = C e^{-kx}}$$

### Aufgabe aus Hausaufgaben pdf

$C$ muss positiv sein, damit die Funktion eine Abnahme beschreiben kann.
$$E(0) = C$$
$$lim_{x\rightarrow\infty}E(x) = 0$$

![[Pasted image 20260423190624.png]]

# 23. Hü, 4.4.2026
## B_447 c)
### 1)
$$\boxed{\frac{dT}{dt} = k \cdot (T_u - T)}$$

### 2)
$$T' + k \cdot T = k \cdot T_u$$

**homogene Lsg**

$$T' + k \cdot T = 0$$
$$T_h = C e^{\lambda t}$$
$$T'_h = \lambda C e^{\lambda t}$$
$$\lambda C e^{\lambda t} + k C e^{\lambda t} = 0$$
$$\lambda = - k$$
$$\boxed{T_h = C e^{-k t}}$$

**partikuläre Lsg**
$$T_p = a$$
$$T_p = 0$$
$$k \cdot a = k \cdot T_u$$
$$a = T_u$$
$$\boxed{T_p = T_u}$$

**allgemeine Lsg**
$$\boxed{T_a(t) = C e^{-k \cdot t} + 20}$$

**spezielle Lsg**
$$10 = C + 20$$
$$C = -10$$
$$12 = -10 e^{-k \cdot 20} + 20$$
$$0,8 = e^{-k \cdot 20}$$
$$-k \cdot 20 = ln(0,8)$$
$$k = - \frac{ln(0,8)}{20} = 0,011$$
$$\boxed{T_s(t) = -10 e^{-0,011 t} + 20}$$

### 3)
$$15 = -10 e^{-0,011 t_{15}} + 20$$
$$0,5 = e^{-0,011 t_{15}}$$
$$\boxed{t_{15} = - \frac{ln(0,5)}{0,011} = 62,13}$$
## B_262 b)
### 1)
$$10 = u_0$$
$$5 = 10 \cdot e^{-k \cdot 20}$$
$$k = - \frac{ln(0,5)}{20} = 0,035$$
$$u(t) = 10 \cdot e^{-0,035 \cdot t}$$

### 2)
![[Pasted image 20260504193831.png|234]]
Da die Änderungsrate negativ sein muss, muss der rechte Term negativ sein. $u$ muss im rechten Term enthalten sein, da die Entladegeschwindigkeit von der aktuellen Spannung abhängig ist.

## B_077 b)
### 1)
$$\int\frac{1}{T_u - T} \,dT = k\int \,dt$$
$u = T_u - T$; $\frac{du}{dT} = -1$; $dT = - du$
$$ln|u| = - k \cdot t + c_1$$
$$T_u - T = C e^{-k \cdot t}$$
$$T = T_u - C e^{-k \cdot t}$$
$$80 = 15 - C$$
$$C = -65$$
$$\boxed{T(t) = 15 + 65 \cdot e^{- 0,8 \cdot t}}$$
## B_077 c)
### 1)
$$T = 40 \cdot e^{-k \cdot t} - 5$$
$$\boxed{T_u = -5°C}$$
### 2)
$$\boxed{T_0 = 35°C}$$

# 24. Hü, am 11.05.26

## SRDP Server Down...

## 10.11

| Merkmal            | Ausprägung |
| ------------------ | ---------- |
| Staatsbürgerschaft | Österreich |
| Alter              | 17 Jahre   |
| Schulstufe         | 8          |
| Körpergröße        | 167cm      |

## 10.12


| Merkmal                            | Typ      | Begründung                                                                            |
| ---------------------------------- | -------- | ------------------------------------------------------------------------------------- |
| Güteklasse eines Hotels            | ordinal  | Wird wahrscheinlich keine Zahl sein, ist aber gemacht um Hotels vergleichen zu können |
| Temperatur                         | metrisch | Eine Zahl                                                                             |
| Beruf                              | nominal  | Es gibt kein eindeutigen weg Berufe zu ordnen                                         |
| Schulbildung                       | ordinal  | Kann man sortieren                                                                    |
| Fahrpreis                          | metrisch | Eine Zahl                                                                             |
| Fahrzeit                           | metrisch | Eine Zahl                                                                             |
| Tabellenplatz eines Fußballvereins | metrisch | Wahrscheinlich in Form einer Zahl                                                     |
| Geschlecht einer Person            | nominal  | Ohne sexistisch zu sein, kann man es nicht Ordnen                                     |
| Einkommen                          | metrisch | Eine Zahl                                                                             |

# 25. Hü, 18.05.26
## 1)
![[Pasted image 20260518205325.png]]


| Name            | Wert                                                             |
| --------------- | ---------------------------------------------------------------- |
| Merkmal         | metrisch                                                         |
| Darstellung     | Liniendiagramm                                                   |
| Grundgesamtheit | offizielle Schlachtungen von Rindern in Österreich im Jahr 2025. |
| Lagemaß         | Absolute Zahlenwerte                                             |


## 10.31
$$\bar{x} = \frac{a}{b} = 12$$
$$\overline{x_1} = \frac{a + 13}{b + 2} = 10$$
$$a = 12 b$$
$$\frac{12b + 13}{b + 2} = 10$$
$$10b + 20 = 12b + 13$$
$$2b = 7$$
$$b = 3,5$$
Falsch?

## 10.32
$$\frac{30 \cdot 49,4 + 20 \cdot 50,2 + 40 \cdot 50,1}{90} = 49,\dot{8}$$

## 10.34
### a)
Wenn alle Werte gleich sind ist der Mittelwert auch dieser Wert.

### b) 
Ja

### c)
Ja

## 10.35
Sortierte Liste:
```
[ 17, 19, 19, 20, 21, 21, 21, 22, 23, 25 ]
```

### a)
$n = 10$
$$\bar{x} =\frac{1}{n} \cdot \sum_{i = 1}^n{x_i} = 20,8$$
$$\tilde{x} = \frac{2 \cdot 21}{2} = 21$$
### b)
Neue Liste:
```
[ 0, 17, 19, 19, 20, 21, 21, 21, 22, 25 ]
```

$$\bar{x} = 18,3$$
$$\tilde{x} = \frac{20 + 21}{2} = 20,5$$
## 10.36

$$\overline{x_A} = 498,75$$
$$\overline{x_B} = 500,125$$
Beide Werte unterscheiden sich kaum (Abweichung von $0,27$%)

# 26. Hü 3.6.2026

## 10.37
3 2 3 1 6 5 4 3 6 2 6 1 3 5 6 1 4 2 4 2

| Gewürfelte Zahl | Absolute Menge |
| --------------- | -------------- |
| 1               | 3              |
| 2               | 4              |
| 3               | 4              |
| 4               | 3              |
| 5               | 2              |
| 6               | 4              |
![[Pasted image 20260608184547.png]]
$$\bar{x} = (3+8+12+12+10+24)/20=3,45$$
$$\tilde x = q_2 = \frac{3+3}{2} = 3$$
$$q_1 = 2$$
$$q_3 = 5$$
(s von einer Stichprobe)
$$s = 1,76$$
$$s^2 = 3,1$$
$$R = 6 - 1 = 5$$
$$d = q_3 - q_1= 5 - 2 = 3$$
![[Pasted image 20260608191029.png]]

## 10.39 a)
$$s=1,10$$
$$s^2 = 1,22$$
$$v = 0,027$$
$$R = 3,1$$
## 10.43
### a)
etwa 52 Minuten

### b)
35 bis 90 Minuten

### c)
45, was heißt, dass er 75% der Einsätze länger als 45 Minuten gedauert haben.

### d)
Weil der Herr Arbeitszeitbetrug begeht, somit nicht die dem Box-Plot zu Grunde liegenden Daten zeigen kann / will, und in einem Box-Plot keinen Absoluten Häufigkeiten angezeigt werden.

## 10.44
### a)
Manche PKWs erfüllen nicht die Mindestprofiltiefe und sollten schleunigst von dem Straßenverkehr entfernt werden.

### b)
Die Profiltiefen der Reifen über dem Durchschnitt von etwa 4,2 mm sind stärker verteilt als die der Unterdurchschnittlichen Reifen.

## 10.45
### a)
75
### b)
25
### c)
25
### d)
0
### e)
0

## 10.46

| h       | mi   | h1   | mi \* hi |
| ------- | ---- | ---- | -------- |
| 2 - 2,5 | 2,25 | 11   | 24,75    |
| 2,5 - 3 | 2,75 | 136  | 371,00   |
| 3 - 3,5 | 3,25 | 329  | 1069,25  |
| 3,5 - 4 | 3,75 | 382  | 1432,50  |
| 4 - 4,5 | 4,25 | 141  | 599,25   |
| 4,5 - 5 | 4,75 | 54   | 256,50   |
| 5 - 5,5 | 5,25 | 11   | 57,75    |
| GESAMT: |      | 1064 | 3814,00  |

## 8.6
Ich würde diese möglichen Ausgänge Wählen

| Wurf 1 | Wurf 2 |
| ------ | ------ |
| 1      | 1      |
| 1      | 2      |
| 1      | 3      |
| 1      | 4      |
| 1      | 5      |
| 1      | 6      |
| 2      | 1      |
| 2      | 2      |
| 2      | 3      |
| 2      | 4      |
| 2      | 5      |
| 2      | 6      |
| 3      | 1      |
| 3      | 2      |
| 3      | 3      |
| 3      | 4      |
| 3      | 5      |
| 3      | 6      |
| 4      | 1      |
| 4      | 2      |
| 4      | 3      |
| 4      | 4      |
| 4      | 5      |
| 4      | 6      |
| 5      | 1      |
| 5      | 2      |
| 5      | 3      |
| 5      | 4      |
| 5      | 5      |
| 5      | 6      |
| 6      | 1      |
| 6      | 2      |
| 6      | 3      |
| 6      | 4      |
| 6      | 5      |
| 6      | 6      |
Hier kommt ein Wurf mit Augensumme $5$, $4$ mal vor
$$P(AS = 5) = \frac{4}{36} = 0,\dot 1 \approx 11 \%$$
## 8.7
### a)
$$P(min\ 1\cdot 6) = \frac{6}{36} + \frac{6}{36} - \frac{1}{36} = \frac{11}{36} = 0,30\dot 5 \approx 30,6\%$$
### b)
Siehe Beispiel **8.6**
### c)
$$P(<=5) = \frac{10}{36} = 0,2 \dot 7 \approx 27,8\%$$
## 8.9
$$P(tie) = 1 \cdot \frac{1}{3} \approx 33\%$$
