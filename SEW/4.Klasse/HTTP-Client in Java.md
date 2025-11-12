Java besitzt seit der Version 11 ein modernes HTTP Client API. Dieses ersetzt die Klasse `HttpURLConnection`, die früher in Java für die HTTP-Kommunikation zuständig war. Das API befindet sich im Package `java.net.http` und besteht aus folgenden Klassen bzw. Interfaces:

## HTTPRequest

Mit dieser Klasse ist es möglich, vollständige HTTP-Methodenaufrufe (`GET`, `POST`, ...) inkl. URL und Daten - zu erstellen. Dabei nutzt die Klasse das [[Builder Pattern]] (Pattern = Entwurfsmuster)

## HTTPClient

Alle mit `HTTPRequest` erstellten Anfragen werden mittels `HTTPClient` gesendet. Wobei diese sowohl synchron als auch asynchron abgesetzt werden können. Synchron bedeutet, dass der Aufruf auf das Ergebnis wartet (blockierend). Asynchron bedeutet, dass nicht auf das Ergebnis gewartet wird, sondern die nächstfolgende Codezeile sofort ausgeführt wird (nicht blockierend).

## HTTPResponse

Diese Klasse repräsentiert die Antwort des Servers. Sie bietet viele hilfreiche Methoden, die wichtigsten aber sind:

* `statusCode()`: Liefert den Status-Code der Antwort
* `body()`: Liefert die Daten der Anfrage

---

Weitere Infos, siehe [baeldung.com](https://www.baeldung.com/java-9-http-client) sowie [Java API-Doc](https://docs.oracle.com/en/java/javase/11/docs/api/java.net.http/java/net/http/package-summary.html)