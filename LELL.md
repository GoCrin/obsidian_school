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


## Problem

-4 + 5
5 * (-1)

Lösungsansatz 1
	bevor irgendwas beginnt werden die characters durch laufen. sollte ein - (oder +) am Anfang der Zeile oder klammer sein wird künstlich ein 0 eingefügt
	**aus -4 + 5 wird 0 - 4 + 5**
	aus 5 * (-1) wird 5 * (0 - 1)