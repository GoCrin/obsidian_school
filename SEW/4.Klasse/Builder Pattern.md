Das Builder-Entwurfsmuster ist eine Möglichkeit Objekte zu erstellen. Es hilft bei der Erstellung unveränderlicher Objekte, die eine große Anzahl von Eigenschaften aufweisen.
Wenn man von einem User-Objekt ausgeht, das 5 "final"-Eigenschaften besitzt (`firstName`, `lastName`, `age`, `phone` und `address`) wovon nur `firstName` und `lastName` verpflichtend sind, führt das zu einer hohen Anzahl von Konstruktoren. (telescoping constructors problem)
Das Builder-Pattern bietet eine elegante Lösung bei der die Unveränderlichkeit der Objekte erhalten bleibt.
```Java
public static void main(String[] args) {
	User user1 = new User.UserBuilder("Bart","Simpson")
		.age(13)
		.phone("1234567")
		.address("Springfield 742 Evergreen Terrace")
		.build();
		
	System.out.println(user1);
	
	User user2 = new User.UserBuilder("James","Bond")
		.age(52)
		.phone("007")
		// keine Adresse
		.build();
	
	System.out.println(user2);
	
	User user3 = new User.UserBuilder("Super","Man")
		// kein Alter
		// keine Telephonnummer
		// keine Adresse
		.build();
	
	System.out.println(user3);
}
```
Die konkrete Implementierung des `UserBuilder` findet sich im Projekt "`BuilderPattern`".