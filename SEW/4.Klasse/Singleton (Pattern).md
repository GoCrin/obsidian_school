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
}
```
