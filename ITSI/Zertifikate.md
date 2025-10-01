# Felder in einem Zertifikat

| Feld                | Bedeutung | Bespiel      |
| ------------------- | --------- | ------------ |
| Subject             |           | htl-hl.ac.at |
| Public key          |           |              |
| Issuer              |           | ZeroSSL      |
| Signature Algorithm |           |              |
| Subject Alt Names   |           |              |
|                     |           |              |

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

