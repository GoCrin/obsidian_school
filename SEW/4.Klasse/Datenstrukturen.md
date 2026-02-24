Datenstrukturen werden benötigt, um Daten zu speichern, zu organisieren und zu verwalten. Sie ermöglichen die effiziente Verarbeitung von Daten und sind grundlegend für die effektive Implementierung von Algorithmen (sortieren, suchen, ...).

---

## Die wichtigsten Vertreter

### List
z.B.:
* LinkedList
* <u>ArrayList</u>(eigentlich keine Liste)

Doppelte Objekte erlaubt, Reihenfolge bleibt erhalten, komfortable Alternative zu Arrays

```Java
List<String> = stringList = new LinkedList<>();
stringList.add("Tim");
```

### Set
z.B.:
* HashSet
* TreeSet

Menge an Objekten, in der jedes Element nur einmal vorkommt.

```Java
Set<String> nameSet = new HashSet<>();
nameSet.add("Tim");
```

### Map
z.B.:
* HashMap
* EnumMap
* TreeMap

Helfen bei der Speicherung von Schlüssel-Wert-Paaren
```Java
Map<String, String> capitalCities = new HashMap<>();
// Add keys and values (Country, City)
capitalCities.put("England", "London");
```

### Queue
Realisierung von FIFO (First in - First out) und  LIFO (Last in - First out) Speichern.

# Konzepte


| Konzept          | -------    | Interface  | ------- | ------- |
| ---------------- | ---------- | ---------- | ------- | ------- |
|                  | List       | Queue      | Set     | Map     |
| Arrays           | ArrayList  |            |         |         |
| Verkettete Liste | LinkedList | LinkedList |         |         |
| Bäume            |            |            | TreeSet | TreeMap |
| Hash             |            |            | HashSet | HashMap |

Man sieht hier wie die Klassen in Java heißen, die ein Interface implementieren und einem Konzept folgen.

```Java
// LinkedList implementiert Queue und List
Queue<String> q = new LinkedList<>();
List<String> l = new LinkedList<>();
```


## Verkettete Liste

Eine verkettete Liste ist eine dynamische Datenstruktur, in der Datenelemente geordnet gespeichert sind

![[Pasted image 20260218121350.png]]