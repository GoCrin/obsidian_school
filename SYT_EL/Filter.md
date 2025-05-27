**Viele Informationen sind noch in [[Frequenz abhängigkeiten]]**
## Formeln
Zeitkonstante $[\tau ] = s$
$$\tau = R*C$$
$$\tau = \frac{L}{R}$$

Grenzkreisfrequenz
$$\omega_g = \frac{1}{\tau}$$
Grenzfrequenz
$$f_g = \frac{\omega_g}{2\pi}$$

## RC-Filter

### Tiefpass
### Hochpass

## RL-Filter

## Beispiele

1\.

![[cbb715bf4590999030c8c0a3288bfadb.png]]

**Bestimme für $R_1 = 1.5k\ohm$ den passenden Kondensator $C_1$ aus der E12-Reihe**

$$\tau = R * C$$
$$-3dB => 100Hz = f_g$$
$$\tau = \frac{1}{2 \pi f_g}$$
$$C = \frac{1}{2 \pi f_g R} = \frac{1}{2 * \pi * 100Hz * 1,5k\ohm} = 1.061 \mu F$$
2\.

Ein RL-Filter soll mit einer Induktivität mit $L = 150\mu H$ aufgebaut werden und eine Grenzfrequenz von $f_g = 7kHz$ besitzen. Berechnen Sie die den notwendigen Widerstandswert

$$R = 2 \pi f_g L = 2 \pi * 7kHz * 150 \mu H \tilde= 6.6\ohm$$

3\.

$R = 5.6k\ohm$ und $f_g = 5.5kHz$, gesucht ist $C$

$$C = \frac{1}{2 \pi f_g R} = \frac{1}{2 \pi * 5,5kHz * 5,6k\ohm} = 5,167nF$$

4\. (Ergebnis nicht überprüft)
Gegeben $C = 220 nF$, $f_g = 600mHz$, gesucht $R$
$$R = \frac{1}{2 \pi f_g C} = \frac{1}{2 \pi * 0,6Hz * 220nF} = 1.2M \ohm$$

5\. (Ergebnis nicht überprüft)
Gegeben: Hoch- & Tieftöner mit jeweils Impedanz von $8 \ohm$ und $f_g = 600Hz$


6\. (Ergebnis nicht überprüft)
Gegeben: Lautsprecher hat nach 1m Entfernung $106dB_{SPL}$, wenn dieser mit 1 Watt elektrischer Leistung angesteuert wird.
Gesucht: Abstand damit Schalldruckpegel $100dB_{SPL}$ nicht überschreitet.
$$ 100dB_{SPL} = 106dB_{SPL} - 6dB * n$$
$$n = \frac{-6dB_{SPL}}{-6dB_{SPL}} = 1$$
$$2^n * 1m = 2^1 * 1m = 2m$$
Schalldruckpegel in 1 Meter wenn Spannung verdoppelt wird.
$$10^{\frac{G}{20}} = 10^{\frac{106}{20}} = \frac{U_{AUS}}{U_{EIN}}$$
$$G = 20 * lg(\frac{U_{AUS}}{U_{EIN}}) = 20 * lg(10^{\frac{G}{20}})$$
$$G_{neu} = 20 * lg(2 * 10^{\frac{G_{alt}}{20}}) = 20 * lg(2 * 10^{\frac{106dB_{SPL}}{20}})$$
$$G_{neu}\ \tilde=\ 112dB_{SPL}$$ 
7\. (Ergebnis nicht überprüft)

| Gegeben             | Lösung                                               |
| ------------------- | ---------------------------------------------------- |
| $G = 20dB$          | $V_U = 10$                                           |
| $G = -20dB$         | $V_U = 0,1$                                          |
| $G = 6dB$           | $V_U\ \tilde=\ 2$                                    |
| $G = -3dB$          | $V_U\ \tilde=\ 0,7$                                  |
| $V_U = 1/10$        | $G = -20dB$ und $A = 20dB$ (A immer $-1 * G$ ~Basti) |
| $V_U = 100$         | $G = 40dB$ und $A = -40dB$                           |
| $G = 12dB$          | $V_U\ \tilde=\ 3,98$                                 |
| $U = 10mV$          | $L_U = -40dbV$                                       |
| $L_U = -60dBV$      | $L_U$ ^= 0,001V                                      |
| $L_U = 80dB(\mu V)$ | $L_U$ ^= 10V                                         |
