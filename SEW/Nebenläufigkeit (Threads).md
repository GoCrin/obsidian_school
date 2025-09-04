Threads ermöglichen einem Programm effizienter zu arbeiten, indem es mehrere Aufgaben gleichzeitig abarbeitet.

## Thread erzeugen
Um einen Thread zu erzeugen, ist zunächst das Interface "`Runnable`" zu implementieren:
```Java
public class BackgroundRunnable implements Runnable {

	@Override
	public void run() {
			System.out.println("Das läuft in einem Thread");	
	}
}
```

## Zugriff auf UI (JavaFX) Komponenten aus einem Thread

JavaFX (und viele andere UI-Frameworks) verwenden einen Thread (Java application thread) um die UI-Komponenten (Buttons, Labels, ...) zu rendern und zu aktualisieren. Von einem anderen Thread darf nicht direkt auf UI-Komponenten zugegriffen werden. JavaFX Events werden automatisch in diesem Thread behandelt, sodass man sich z.B. bei einem Buttonklick nicht speziell darum kümmern muss.
Möchte man jedoch von einem anderen Thread auf eine UI-Komponente zugreifen, muss man diesen Zugriff in den JavaFX Application Thread "einhängen"
Dafür kann der statischen Methode `Platform#runlater(...)` ein entsprechendes `Runnable` übergeben werden:
```Java
Platform.runlater(new Runnable() {
	@Override
	public void run() {
		tuneButton.setText("Tune");
	}
});
```
Um zu überprüfen, ob der aktuelle Programmcode im Application Thread ausgeführt wird oder nicht, kann die Methode `Platform#isFxApplicationThread()` verwendet werden
```Java
boolean isFxThread = Platform.isFxApplicationThread();
```
