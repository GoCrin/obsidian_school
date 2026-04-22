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
$$$$
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
