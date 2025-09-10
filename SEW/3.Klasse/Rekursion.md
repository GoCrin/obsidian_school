Rekursion ist eine Methode bei der eine Funktion sich selbst aufruft. Diese Vorgehensweise bietet eine Möglichkeit, komplizierte Probleme in einfachere Teilprobleme zu zerlegen, die leichter zu lösen sind.

Beispiel: Fibonacci Zahlen
![[Pasted image 20250409083439.png]]
Es ergibt sich für die ersten n folgender Werteverlauf

| n      | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   |
| ------ | --- | --- | --- | --- | --- | --- | --- | --- |
| fib(n) | 1   | 1   | 2   | 3   | 5   | 8   | 13  | 21  |
Berechnet die Fibonacci Stelle n:

```
public int fib(int n) {
	if (n == 1) {
		return 1;
	}
	if (n == 2) {
		return 1;
	}
	return fib(n - 1) + fib(n - 2);
}
```

Bsp: n = 4

![[Pasted image 20250409084248.png]]
