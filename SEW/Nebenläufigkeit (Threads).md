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