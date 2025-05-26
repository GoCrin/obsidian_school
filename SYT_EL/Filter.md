## Größen
Zeitkonstante
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

**Stimmt nicht**

$$C = \frac{1}{2 \pi f_g R} = \frac{1}{2 \pi * 5,5kHz * 5,6k\ohm} = $$