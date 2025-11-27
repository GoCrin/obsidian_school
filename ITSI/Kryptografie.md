Block-Chiffren -> sind auf bestimmte länge (z.B. 128 bit) definiert.
Strom-Chiffren -> können einen Strom von Bytes verschlüsseln. (RC)

# Symmetrische Verschlüsselung
## AES
* meist verwendete symmetrische Chiffre.
* NIST gibt bekannt, dass sie einen Verschlüsselungsalgorithmus mit bestimmten Spezifikationen brauchen.

Anforderungen an die Kandidaten:
* Blockchiffre mit 128 Bit Blockgröße
* Unterstützung von 3 Schlüssellängen: 128, 192, 256 bit
* Sicher ggü. kryptoanalytischen Angriffen
* Effizient in Soft- Hardware

5 Finalisten im August 1999:
* Mars - IBM Corporation
* RC6
* Rijndael
* Serpant
* Twofish

Fast jeder Block-Chiffren verwendet eine Funktion die **mehrmals** ausgeführt wird (**Runden**). Man kann an der Anzahl der Runden sehr leicht erkennen welcher symmetrischer Block-Chiffre verwendet wird.

* Key-Additions-Schicht
* Runde:
	* Byte-Substitution
	* ShiftRows-Unterschicht
	* MixColumn-Unterschicht
	* Key-Additions-Schicht

Eingangstext (128 Bit) muss als 4x4 Byte Matrix dargestellt werden.

|       | Spalte |     |     |     |
| ----- | ------ | --- | --- | --- |
| Reihe | A0     | A4  | A8  | A12 |
|       | A1     | A5  | A9  | A13 |
|       | A2     | A6  | A10 | A14 |
|       | A3     | A7  | A11 | A15 |
A0 ... A15 sind die 16 Byte.

### Rundenfunktion

**Byte-Substitution**
Jedes Element der Eingangsmenge muss genau einem Element der Ausgangsmenge zugeordnet werden (**bijection oder Bijektive Funktion**).
Verwendet eine Tabelle (S-Box) mit 256 oder 16\*16 Elementen. 2 

Seitenkanalangriff: Stromverbrauch während der Verschlüsselung Messen, oder Dauer der verschlüsselung.

## KDF key derivation function
