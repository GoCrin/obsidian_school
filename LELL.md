```
main {
	user_input
	builtin_commands
		exit
		..
		calc
	externel_bin
}

calc -> anyNumber(int or float) {
	
}
```


## Problem 1

-4 + 5
5 * (-1)

Lösungsansatz 1
	bevor irgendwas beginnt werden die characters durch laufen. sollte ein - (oder +) am Anfang der Zeile oder klammer sein wird künstlich ein 0 eingefügt
	**aus -4 + 5 wird 0 - 4 + 5**
	aus 5 * (-1) wird 5 * (0 - 1)

## Problem 2
Wie repräsentier ich Klammern jetzige Rechnungen werden in: Zahlenliste und Operatorliste gespeichert
```
zahlen
operatoren

für operatoren als op {
	nimm index von op
	nimm zahl von zahlen an index von op und führe operation mit 
	zahl an 1 + index von op durch
	...
}
```
So lässt es nicht wirklich klammern zu.

4 * (2 + 3)

Lösungsansatz 1
	KA.