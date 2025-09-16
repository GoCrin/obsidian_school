Ist ein Standard für Zertifikate
Zertifikat issuer signiert Subject & Public key -> stellt sicher, dass Webpage ist wer sie vorgibt zu sein, in dem Signatur garantiert, dass Private- / Public key wirklich der richtigen "Person" gehört

# HTTPS

* Secure http -> tls verschlüsselt
* ist n - n verschlüsselt
* Schlüssel muss sich ausgemacht werden -> Man in the middle attack

# Zertifikate in Firefox
1. Schloss neben URL
2. Connection Secure drücken
3. More information
4. View Certificate

* Dauer der Gültigkeit ist heutzutage kurz -> wird mit scripts erneuert
* Subject Alt Names -> haben (bei htl-hl) das exakt gleiche Zertifikat
* **Public key -> ZeroSSL bestätigt mit Signatur, dass das der richtige Public key ist**
* **Signature Algorithm**
* Key Usages -> Digital Signature oder Andere CAs signieren

# PKI (Public-Key-Infrastruktur)

Chain of trust:

* Certificate
	* Subject: htl-hl.ac.at
	* Issuer: ZeroSSL
* CA
	* Subject: ZeroSSL
	* Issuer: UserTrust
* Root CA
	* Subject: UserTrust
	* Issuer: UserTrust

Browser bekommen die gaze chain
* Schaut Subject an
* Sucht CA Subject der gleich ist wie Issuer vom 1. CA -> Prüft mit PK von 2. CA die Signatur vom 1. CA
* Dieser Vorgang wird bis zu einem Root CA wiederholt

Manche mobile Apps überprüfen Chains of trust nicht gut / vollständig
## Intermediate CA
Signieren Endanwender
## root CA
Signieren Intermediate CAs
Signieren sich selbst

# Arten von Zertifikaten
* Selbst Signierte
* Wildcard -> Subject enthält Wildcards (z.B. "\*.htl-hl.ac.at")

# Beantragen
1. Public / Private Key-Pair erstellen
2. CSR (Certificate signing request): Subject + Public key
3. schicken an CA: signieren das Zertifikat
4. CA Schicken C zurück