# Packing

Eigentliches Binary wird archiviert und ein Unpacker wird am Anfang des Progamms angehängt. Dieser entpackt das eigentliche Programm wieder damit es ausgeführt werden kann.

Das packing hat zur Folge, dass man das richtige Programm in Debuggern wie Ghidra nicht direkt lesen kann.

## Ablauf bei Start eines gepacketen Programmes

1. OS startet entry point: Loader wird gestartet
2. Loader unpacked EXE in einer Sektion des RAM
3. Loader führt das entpackte Programm im RAM aus.
4. Das "originale" EXE läuft

## Anti-Packing

1. Drop EXE from RAM
2. Use existing Unpacker

# Obfuscation

Ein "Obfuscator" ändert alle variablen namen, damit man deren Sinn nicht erkennen kann.

