# Ableitungen weiterer Grundfunktionen
* **Exponentialfunktion**

|              |                       |
| ------------ | --------------------- |
| $f(x) = e^x$ | $f'(x) = e^x$         |
| $f(x) = a^x$ | $f'(x) = a^x * ln(a)$ |

* **Logarithmusfunktion**

|                     |                             |
| ------------------- | --------------------------- |
| $f(x) = ln(x)$      | $f'(x) = \frac{1}{x}$       |
| $f(x) = log_{n}(x)$ | $f'(x) = \frac{1}{x*ln(n)}$ |

* **Kreis Funktionen**

|                 |                              |
| --------------- | ---------------------------- |
| $f(x) = sin(x)$ | $f'(x) = cos(x)$             |
| $f(x) = cos(x)$ | $f'(x) = -sin(x)$            |
| $f(x) = tan(x)$ | $f'(x) = \frac{1}{cos^2(x)}$ |
x in Bogenmaß

* **Arkusfunktionen**

|                    |                                              |
| ------------------ | -------------------------------------------- |
| $f(x) = arcsin(x)$ | $f'(x) = \frac{1}{\sqrt{1-x^2}}; \|x\| < 1$  |
| $f(x) = arccos(x)$ | $f'(x) = -\frac{1}{\sqrt{1-x^2}}; \|x\| < 1$ |
| $f(x) = arctan(x)$ | $f'(x) = \frac{1}{1+x^2}$                    |

# Ableitungsregeln
* **Faktorregel (FR)**
$y = k * f(x)$
$y' = k * f'(x)$
$k$ -> Konstante
---
* **Summenregel (SR)**
$y = f(x) +- g(x)$
$y' = f'(x) +- g'(x)$
---
* **Produktregel (PR)**
$y = f(x) * g(x)$
$y' = f'(x) * g(x) + f(x) * g'(x)$
---
* **Quotientenregel (QR)**
$y = \frac{f(x)}{g(x)}$
$y' = \frac{f'(x) * g(x) - f(x) * g'(x)}{g^2}$
---
* **Kettenregel (KR)**
$y = f(u)$ & $u = g(x)$
also: $f(g(x))$
dann gilt:
$y' = f'(u) * g'(x)$
