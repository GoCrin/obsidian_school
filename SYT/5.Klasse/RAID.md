Redundant Array of Independent (Inexpensive) Disks

Verbindet mehrere physische Festplatten zu einer logischen. Kann auch redundant Dateien speichern, wozu es heute im Endverbraucherbereich meist verwendet wird.

## RAID Levels

$n$ ... Mögliche Anzahl an Festplatten
$C_G$ ... Gesamtkapazität
$c_0$ ... Kapazität einer Festplatte

Arten wie man die Festplatten verbunden werden und redundant speichern.

(JBOD schließt nur Festplatten zusammen, ohne Redundanz)

### Level 0 Striping

n >= 2 ... anzahl der festplatten 
C gesamt kapazität = c_i kapazität einer festplatte \* n
$$n \geq 2$$
$$C_G = c_0 \cdot n$$


Man teilt die Dateien in Streifen die eine fixe stripe-size hat z.B. 1Byte, diese Streifen werden dann etwa gleichmäßig auf die physischen Festplatten aufgeteilt. Ausnahmen sind Dateien, die kleiner als die stripe-size sind. Wenn die Lesegeschwindigkeit das Bottleneck im system bildet, kann sie mit diesem level vervielfacht werden, da man ja mehrere Festplatten gleichzeitig liest. Wenn eine Festplatte kaputt ist, werden alle Dateien unbrauchbar.

### Level 1

$$n \geq 2$$
$$C_G = c_0$$
n >= 2
C = c_0

Macht wie bei level 0 stripes, aber speichert jeden stripe auf jede Festplatte

### Level 2, 3 & 4 
Werden von keinem kaufbaren Controller unterstützt.

Man berechnet immer parity data, aber die art wie und wo man diese speichert hat sich mit Level 5 durchgesetzt.

### Level 5

n >= 3
C_G = c_= \* (n - 1)

$$n \ge 3$$
$$C_G = c_0 \cdot (n - 1)$$

Stripe 1 auf Festplatte A, Stripe 2 auf B und 1 xor 2 auf C. Es wird vermutet, dass der Startpunkt bei den nächsten 2 stripes rotiert und dann Festplatte B ist. Es wurde nicht geklärt was mit dem Ende der Datei passiert, wenn es nicht sauber nach dem Verfahren aufgeteilt werden kann. 

Es werden immer n -1 Stripes gespeichert, dann dies xor'ed auf die "letzte" Festplatte.
Also bei 4 Festplatten (A,B,C,D):
Stripe 1 auf A, Stripe 2 auf B, Stripe 3 auf C und 1 xor 2 xor 3 auf D. Danach wird wieder rotiert.

### Level 6

$$n \ge 4$$
$$C_G = c_0 \cdot (n -2)$$

Es werden mehr Paritätsdaten berechnet, dafür dürfen aber auch 2 Festplatten ohne Datenverlust ausfallen 


Hardware vs Software Raid

Hardware war früher performanter, als Software RAID, aber heutzutage ist das nicht mehr so. Wodurch Hardware Raid controller nur noch im Serverbereich verwendet werden. 

# Ka

Controller Mode: HBA
Alles wird os überlassen, RAID ist aus