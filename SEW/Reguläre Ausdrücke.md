**Zum Üben:** [regex101](https://regex101.com/)
Reguläre Ausdrücke (engl. regular expressions) auch Regex genannt, sind Zeichenketten auf Basis syntaktischer Regeln, die es ermöglichen, Zeichenfolgen zu beschreiben.
**z.B.:** Bei einem String soll überprüft werden, ob er nur bestimmte Zeichen enthält sowie eine Länge $\geq$ 1 Zeichen aufweist. Zulässig sind: Buchstaben (ASCII a-z), Ziffern, spezifische Sonderzeichen.
**Lösung:**
```
^[A-Za-z0-9%!=#]+$
```

## Notation

| Ausdruck                       |                                    |
| ------------------------------ | ---------------------------------- |
| s (Beliebiges Zeichen)         | Zeichen s (kein Spezialsymbol)     |
| \s                             | Zeichen s                          |
| .                              | Alle Zeichen außer Zeilenende      |
| ^                              | Zeilenanfang                       |
| $                              | Zeilenende                         |
| [$s_1 ... s_n$]                | alle Zeichen in {$s_1 ... s_n$}    |
| [^$s_1 ... s_n$]               | alle Zeichen außer {$s_1 ... s_n$} |
| r* (r ist Zeichen oder Gruppe) | null Mal oder öfter r              |
| r+                             | ein Mal oder öfter r               |
| r?                             | null oder ein Mal r                |
| r{i}                           | i Mal r                            |
| r{i,}                          | mindestens i Mal r                 |
| r{i,j}                         | i bis j Mal r                      |
| $r_1$$r_2$                     | $r_1$ gefolgt von $r_2$            |
| $r_1$ \| $r_2$                 | $r_1$ oder $r_2$                   |
| (r)                            | r (Gruppierung)                    |
