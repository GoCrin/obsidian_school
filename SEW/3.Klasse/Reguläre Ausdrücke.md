**Zum Üben:** [regex101](https://regex101.com/)
Reguläre Ausdrücke (engl. regular expressions) auch Regex genannt, sind Zeichenketten auf Basis syntaktischer Regeln, die es ermöglichen, Zeichenfolgen zu beschreiben.
**z.B.:** Bei einem String soll überprüft werden, ob er nur bestimmte Zeichen enthält sowie eine Länge $\geq$ 1 Zeichen aufweist. Zulässig sind: Buchstaben (ASCII a-z), Ziffern, spezifische Sonderzeichen.
**Lösung:**
```
^[A-Za-z0-9%!=#]+$
```

## Notation

| Ausdruck                       | Bedeutung                          |
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

## Syntaxdiagramm
[regulex](https://jex.im/regulex), [Regex Vis](https://regex-vis.com/)
Ein regulärer Ausdruck kann auch als Syntaxdiagramm dargestellt werden. Das Syntaxdiagramm beschreibt den regulären Ausdruck, indem es in grafischer Form zeigt, welche Strings gebildet werden können.

| Syntaxdiagramm                       |      |
| ------------------------------------ | ---- |
| ![[Pasted image 20250507081209.png]] | A    |
| ![[Pasted image 20250507081242.png]] | \s   |
| ![[Pasted image 20250507081424.png]] | A+   |
| ![[Pasted image 20250507081609.png]] | A\*  |
| ![[Pasted image 20250507081747.png]] | AB   |
| ![[Pasted image 20250507081853.png]] | A\|B |
| ![[Pasted image 20250507082218.png]] | A?   |

Beispiel:
![[Pasted image 20250507082426.png]]

## Verwendung in Java

```
String regularExpression = "^[A-Za-z0-9%!=#]+$";
String stringToValidate = "3BHITS";

//1. Möglichkeit
if (stringToValidate.matches(regularExpression)) {
	System.out.printf("%s is valid.\n", stringToValidate);
}

//2. Möglichkeit
Pattern pattern = Pattern.compile(regularExpression);
if (pattern.matcher(stringToValidate).matches()) {
	System.out.printf("%s is valid.\n", stringToValidate);
}
```

Die 1. Möglichkeit ist simpel und gut, aber wenn man immer wieder gegen das selbe Muster "matched" sollte man die 2. Möglichkeit verwenden.