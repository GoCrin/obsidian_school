Eines der Kernprinzipien der objektorientierten Programmierung, die Vererbung, erlaubt es, existierenden Code wiederzuverwenden oder bestehende Klassen zu erweitern. Klassen können von anderen Klassen abgeleitet werden und erben damit alle Eigenschaften und Methoden der Oberklasse
![[Pasted image 20250908183116.png]]

In Java kann eine Klasse nur von **einer** Oberklasse aberben (einfache Vererbung)

Zum Ausführen der ursprünglichen Methode in der abgeleiteten Klasse wird in der überschriebenen Methode das Schlüsselwort `super` verwendet.

```Java
class Wesen {
	public void schrei() {/*...*/}
}

class Hund extends Wesen {
	@Override
	public void schrei() {
		super.schrei();
		/*...*/
	}
}
```
