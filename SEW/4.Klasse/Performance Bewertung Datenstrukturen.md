Performance der Datenstrukturen im schlechtesten Fall:

| Datenstuktur             | Zugriff              | Einfügen    | Löschen     | Suchen      |
| ------------------------ | -------------------- | ----------- | ----------- | ----------- |
| Array(List)              | $O(1)$               | $O(1)$      | $O(n)$      | $O(n)$      |
| Sortiertes Array         | $O(1)$               | $O(1)$      | $O(log(n))$ | $O(log(n))$ |
| LinkedList               | $O(n)$               | $O(1)$      | $O(n)$      | $O(n)$      |
| Baum                     | $O(n)$               | $O(1)$      | $O(n)$      | $O(n)$      |
| Balancierte Baum         | $O(log(n))$          | $O(log(n))$ | $O(log(n))$ | $O(log(n))$ |
| HashMap                  | $\rightarrow$ Suchen | $O(log(n))$ | $O(log(n))$ | $O(log(n))$ |
| HashMap ohne Kollisionen | $\rightarrow$ Suchen | $O(1)$      | $O(1)$      | $O(1)$      |

Die Performance der HashMap bei Verwendung von Listen im Kollisionsfall beträgt $O(n)$. In Java wird jedoch ab einer gewissen Anzahl von Elementen ein balancierter Baum verwendet, dadurch beträgt die Performance $O(log(n))$.