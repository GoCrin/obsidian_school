hash-only-1 in picoctf

ls -> flaghasher
file flaghasher -> **setuid** ELF 64-bit ...
ls -l -> -rwsr-xr-x flaghasher
./flaghasher
schreibt irgendwas in /root/

strings flaghasher

## Rainbowtabels

Dadurch, dass jeder Hash-Algorithmus bei selben input immer den selben output gibt, kann man für viele bekannte Passwörter mit diesem Algorithmus hashen und mit der gewonnen Liste auf den ursprünglichen Wert eines gegebenen Hash's zurück schließen.
[crackstation](https://crackstation.net/)
## Salzen

Um Rainbowtabels unbrauchbar zu machen "salzt" man den Input (z.B. Passwörter) bevor man ihn hasht. Dieses Salz ist nicht geheim.