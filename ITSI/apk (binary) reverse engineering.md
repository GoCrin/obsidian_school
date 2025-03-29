
| Programm | Funktion                                                                 | Beispiel                             |
| -------- | ------------------------------------------------------------------------ | ------------------------------------ |
| file     | Datentyp einer Datei herausfinden                                        | file clib/a.out                      |
| strings  | Menschenlesbare strings in Bytefiles                                     | strings clib/a.out                   |
| xxd      | hex editor                                                               | xxd clib/a.out                       |
| Ghidra   | disassambler (von binary auf assambly)                                   |                                      |
| xargs    | nimmt (Liste an) Argumente(n) und führt damit als Input einen Befehl aus | find . -type f \| xargs file \| less |
Ghidra (von NSA) um binarys auf assambly zu decompilen

file (dateityp finden)
strings (Menschenlesbares in Bytefiles)
xxd (hex editor)

file verwenden -> format herausfinden -> googlen wie man entpackt
7zip installieren -> damit apk entpacken


xargs nimmt input und führt mit diesem befehle aus. In dem Fall nimmt es jede Datei aus dem WD und gibt aus welchen Dateityp diese haben


