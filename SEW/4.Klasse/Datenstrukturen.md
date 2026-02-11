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
z.B.:

```Java
//soon
```