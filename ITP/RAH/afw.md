# DOM
Document Object Model

## HTML DOM

Das HTML DOM ist die Repräsentation der HTML Datei in Form einer Baumstruktur besteht aus Objekten (HTML Elemente), Atributen und Events. Objekte besitzen Atribute und "feuern" Events. Programmiersprachen (wie JavaScript) können auf die Atribute von Objekten zugreifen um diese zu lesen oder zu verändern und auf Events reagieren.


In folgendem Beispiel wäre das DOM: `html` -> `body` -> `p` -> "HALLO", wobei `p` einen Atribut namens "style" besitzt
```Html
<html>
<body>

	<p style="border: 2px solid black;">
		HALLO
	</p>

</body>
</html>
```
### HTML DOM Document

ist ein Objekt Namens `document`, welches Funktionen zur Suche und Manipulation des DOM bereitstellt. 

Angenommen man hat eine HTML Datei mit folgendem Inhalt.
```HTML
<html>
<body>

<h1>Überschrift</h1>
	<h2 class="topic_x">Überschrift</h2>
		<!-- TEXT -->
	<h2 class="topic_x">Überschrift</h2>
		<!-- TEXT -->

<h1>Überschrift</h1>
	<h2 id="special_h2">Überschrift</h2>
		<!-- TEXT -->
<h1>Überschrift</h1>
	<!-- TEXT -->

</body>
</html>
```

Nun können die `<h1>` und `<h2>` Elemente über `document` gefunden werden.


```JavaScript
// Finden & Speichern der besonderen Überschrift
let special_header = document.getElementById("special_h2");
// Bearbeiten der Überschrift
special_header.innerHTML = "Besondere Überschrift";

// Änderen eines Attributes
// Klassen namen aller Elemente mit klasse topic_x von topic_x auf topic_y änderen
document.querySelectorAll(".topic_x").forEach((e) => {
	e.setAttribute("class","topic_y");
});
// Den Hintergrund aller topic_y Überschriften ändern
document.querySelectorAll(".topic_y").forEach((e) => {
	e.setAttribute("style","background-color: red;");
});

// Speichern aller h1 elemente in einer Variable
let all_header_one = document.getElementsByTagName("h1");
```


#### Asynchronisierung 

##### Promises

Promises (dt. Versprechen) sind Javascript Objekte, welche asynchrone Tätigkeiten durchführen.
Der Konstruktor eines `Promise` erwartet einen `executor`, welcher selbst 2 Felder hat. Das 1. Feld ist `resolve` und das 2. `reject`. Im `executor` befindet sich die Logik die der `Promise` abarbeitet.

```JavaScript
// Erstellen des Versprechen
let myPromise = new Promise((resolve, reject) => {
	let success = true;
	
	// Irgendeine Logik (die success ändern könnte)
	
	if (success) {
		resolve(67);
	} else {
		reject();
	}
});
```

ein `Promise` hat 2 Instanzvariablen. `state` und `result`

| state     | result                 |
| --------- | ---------------------- |
| pending   | undefined              |
| fulfilled | Irgendein Ergebniswert |
| rejected  | Ein Error Objekt       |

nun kann mit der Funktion `myPromise.then()` das Ergebnis vom Versprechen behandelt werden. Hier sollte auf das Ende des Versprechens gewartet werden. 

```JavaScript
myPromise.then(
	(value) => { /* Behandlung des Ergebnisses */ },
	(error) => { /* Behandlung des Fehlers */ }
);
```

Die Variablen `value` und `error` sind vorgegeben.

##### Async / Await

`async` ist ein keyword, welches Funktionen ein `Promise` zurück geben lässt.
`await` kann nur innerhalb einer asynchronen (`async`) Funktion verwendet werden und hat zur Folge, dass auf das "Ende" eines Versprechens (`Promise`) gewartet wird.

```JavaScript
async function update_joke() {
    try {
	    //holt sich von einer freien API einen Witz im JSON Format
	    let joke = await fetch("https://sv443.net/jokeapi/v2/joke/Any");
        let respone = await joke.json();

		// Falls bei der API ein Fehler auftritt
        if (respone.error) {
          return;
        }
        
        // Setze den Text eines Elements auf den Witz
        let joke_space = document.getElementById("joke");
        switch (respone.type) {
          case "single":
            joke_space.innerHTML = respone.joke;
            break;
          case "twopart":
            joke_space.innerHTML = respone.setup + "<br>" + respone.delivery;
            break;
        }
    } catch (e) {
	    console.log(e);
    }
}

document.getElementById("get_joke").addEventListener("click", () => {
	update_joke();
});
```
Dieses Script setzt einen Knopf mit der id "get_joke" und einen Element mit der id "joke" voraus. `fetch()` ist ähnlich wie `curl` und Webbrowser, da es den Inhalt der angegebenen URL ausgibt.