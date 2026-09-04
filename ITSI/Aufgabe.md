1. Entropie prüfen (ist sehr hoch → packed)

```
binwalk -E app.elf
```

## Packed ELF unpacken

Programm im Hintergrund starten.
```
./app.elf &
```

So speichert man sich die process-id in die Variable `PID_APP`
```
PID_APP=$!
```

So sieht man alle "Sektionen" des Programms.
```
pmap -x $PID_APP | less
```
Die Zeilen schauen etwa so aus:
```
Address           Kbytes     RSS   Dirty Mode  Mapping  
0000000000400000      40      40      40 r-x--   [ anon ]
```
Hier muss man sich eine Zeile suchen die als mode executable hat, eine typische Größe hat (hier 40kB) und (ich glaube) "anon" als Mapping hat.
Die gefundene Adresse kann jetzt hier bei `skip` verwendet werden und die Größe (40 \* 1024 in hex) bei `count`.
```
sudo dd if=/proc/$PID_APP/mem of=dump_app bs=1 skip=$((0x400000)) count=$((0xa000))
```