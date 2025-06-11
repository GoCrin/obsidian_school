Threads ermöglichen einem Programm effizienter zu arbeiten, indem es mehrere Aufgaben gleichzeitig abarbeitet.

## Thread erzeugen
Um einen Thread zu erzeugen, ist zunächst das Interface "`Runnable`" zu implementieren:
```
public class BackgroundRunnable implements Runnable {

	@Override
	public void run() {
			System.out.println("Das läuft in einem Thread");	
	}
}
```

## Zugriff auf UI (JavaFX) Komponenten aus einem Thread

JavaFX (und viele andere UI-Frameworks) verwenden einen Thread (Java application thread) um die UI-Komponenten (Buttons, Labels, ...) zu rendern und zu aktualisieren. Von einem anderen Thread darf nicht direkt auf UI-Komponenten zugegriffen werden.