# Felder in einem Zertifikat

| Feld                | Bedeutung                                                              | Beispiel           |
| ------------------- | ---------------------------------------------------------------------- | ------------------ |
| Subject             | (Domain) Name des Zertifikatbesitzers (z.B. htl)                       | htl-hl.ac.at       |
| Public key          | Public key des Zertifikatbesitzers                                     |                    |
| Issuer              | wer das Zertifikat austellt                                            | ZeroSSL            |
| Signature Algorithm | Mit welchem Algorithmus das Zertifikat (der Hash davon) signiert wurde | SHA-256 ECDSA      |
| Subject Alt Names   | Liste an Subjects die auch von dem Zertifikate zertifiziert sind       |                    |
| Validity            | Dauer der Gültigkeit, des Zertifikates                                 |                    |
| Key Usage           | Was man mit seinem signierten Key machen darf                          | Digital Signature, |

# Arten von Zertifikaten

## Wildcard-Zertifikate

Das "Subject" Feld darf Wildcards enthalten. z.B.:

```
*.htl-hl.ac.at
```

## Selbst signierte Zertifikate

Das sind Zertifikate die nicht von einer anderen CA (Certificate Authority) signiert sind, sondern mit dem eigenen private key signiert sind. Diese Art von Zertifikat ist quasi nur bei Root CA's sinnvoll.

# X.509

Ist ein Standard für die Erstellung von Zertifikaten, bei der eine Certificate Authority (CA) entweder über einen Eintrag im Webroot (eines Servers) oder ein DNS (TXT) Record überprüft ob einer Person eine bestimmte domain gehört. Ist dieser Besitz bewiesen, Signiert die CA den Public Key (und alle anderen Zertifikatfelder -> hashed) des Zertifikat-Beantragenden.

# Chain of Trust

Ist eine Kette von einer vom Browser vertrauten Root CA bis zu einem Leaf Zertifikat. Diese Kette wird gebildet in dem jedes Zertifikat (diese enthalten den Public Key des Besitzers) von der nächst höheren CA bis zur Root CA signiert wird. Die Root CA darf sich selbst signieren, da der Browser dieser CA direkt vertraut.

## Leaf Zertifikat 

Ist ein Zertifikat, das keine anderen Zertifikate ausstellen darf.
# acme.sh

acme.sh ist ein bashscript, mit dem man automatisiert Zertifikate beantragen und erneuern kann.

## Installation

Herunterladen
```Bash
su -
curl https://get.acme.sh | sh -s email=my@example.com
```

Einen alias erstellen (Befehl unvollständig)
```Bash
alias acme.sh='/root/'
```

## Zertifikat beantragen (CSR = Certificate Signing Request)

```Bash
acme.sh --issue -d guebe.moo.com -w /var/www/vps-28535c5d.vps.ovh.net
```

Dieser Befehl führt Folgende Aufgaben durch
* keypair erstellen
* CSR mit angegebenen Daten erstellen


Zeigt an was im CSR ist
```Bash
openssl req -text -in guebe.mooo.com.csr | less
```

* Subject
* Domain
* Pub key
* Extended Key usage
* Subject Alternative Name

Geht die ganze fullchain durch und gibt alle Zertifikate aus
```Bash
openssl storeutl -text -certs fullchain.cer | less
```

# PicoCTF

## ReadMyCert

