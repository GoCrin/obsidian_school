```Java
try {
	//int wert = Integer.valueOf("S");
	int wert = Integer.valueOf("10");
	ArrayList<String> list = null;
	list.add("hi");
} catch (NumberFormatException e) {
	System.err.println(e.getMessage());
} catch (NullPointerException e) {
	System.err.println(e.getMessage());
}
```

Tritt bei der Abarbeitung der Anweisung des try-Blocks ein Fehler auf, der eine Exception auslöst, so stoppt die Verarbeitung der Anweisung im try-Block. Gibt es einen passenden catch-Block wird dieser ausgeführt. Sonst wird die Exception weiter gegeben bis das Programm abbricht.