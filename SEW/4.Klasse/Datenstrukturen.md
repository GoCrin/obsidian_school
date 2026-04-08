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

## Binäre Baum

![[Pasted image 20260225121143.png]]

## Hashmap
Bsp: Hashfunktion: h = wert % 5

![[Pasted image 20260311115520.png|482]]

```java
public class SetDemo {
	public SetDemo() {
		// Create a Set object called nameSet with unique names
		Set<String> nameSet = new HashSet<>();
		
		// Add values to Set
		System.out.println("Add values to Set ...");
		nameSet.add("Florian");
		nameSet.add("Sepp");
		nameSet.add("Kurt");
		
		System.out.printf("Size: %d\n", nameSet.size());
		
		// Check if an item exists
		System.out.printf("Does 'Kurt' exist? %s!\n", nameSet.contains("Kurt") ? "YES" : "NO");
		
		// Remove an entry
		System.out.println("Remove an entry ...");
		nameSet.remove("Sepp");
		System.out.printf("Size: %d\n", nameSet.size());
		
		// Loop through Set
		for(String name : nameSet) {
			System.out.printf("  Name: %s\n", name);
		}
		
		// Clear Set
		System.out.println("Clear set ...");
		nameSet.clear();
		System.out.printf("Size: %d\n", nameSet.size());
	}

	public static void main(String[] args) {
		new SetDemo();
	}
}
```

Student POJO
```java
public class Student {
	
	// Fields *****
	
	private String firstName;
	private String lastName;
	
	// Instance creation ******
	
	public Student(String firstName, String lastName) {
		this.firstName = firstName;
		this.lastName = lastName;
	}
	
	// Accessors ******
	
	// TODO: generate getter + setter
	
	// hash code + equals generate
}
```

```java
public class SetDemoWithPojo {
	
	public SetDemoWithPojo() {
		
		// Create a Set object to hold students
		Set<Student> studentSet = new HashSet<>();
		
		Student albert = new Student("Albert", "Einstein");
		
		studentSet.add(albert);
		
		boolean doesAlbertExist = studentSet.contains(albert);
		System.out.printf("Does ALbert exist?: %s\n", doesAlbertExist);
		
		doesAlbertExist = studentSet.contains(new Student("Albert", "Einstein"));
		System.out.printf("Does ALbert exist?: %s\n", doesAlbertExist);
	}
	
	public static void main(String[] args) {
		new SetDemoWithPojo();
	}
}
```