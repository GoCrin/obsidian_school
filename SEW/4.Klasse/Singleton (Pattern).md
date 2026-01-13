Das Entwurfsmuster "Singleton" stellt sicher, dass von einer Klasse genau ein Objekt existiert.
Implementierung (lazy-Initiazation)

```java
public class MySingleton {
	private static MySingleton instance;
	
	private MySingleton() {
	}
	
	public static synchronized MySingleton getInstance() {
		if (instance == null) {
			instance = new MySingleton();
		}
		return instance;
	}
	
	public int getValue() {
		//...
	}
}
```
Das Schlüssel wort `synchronized` stellt sicher, dass der Singleton nur 1x instanziiert wird (Thread sicher).

Zugriff aus anderer Klasse: `MySingleton.getInstance().getValue()`

Alternative Implementierung mittels enum:
```Java
public enum MySingleton {
	INSTANCE;
	public MySingleton getInstance() {
		return INSTANCE;
	}
	
	//Other methods
	public int getValue() {
		//...
	}
}
```

# Anwendungsbeispiele
* Zugriff auf eine zentrale Logging-Funktionalität in eine Date

# Vorsicht
Eine Singleton Implementierung sollte sehr sparsam eingesetzt werden, da die Gefahr besteht, quasi ein Äquivalent zu  globalen Variablen zu schaffen. Die Testbarkeit wird darüber hinaus sehr erschwert.