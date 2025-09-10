Bei Vererbung wird Spezialisierung abgebildet, be Interfaces die Funktionalität. Klassen können mehrere Interfaces implementieren

```Java
public interface Resizeable {
	public abstract void resize();
}

public class Cube implements Resizeable {
	@Override
	public void resize() {
	//...
	}
}
```