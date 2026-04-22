Ab [[Unveränderliche Objekte oder Immutable Objects]] bis [[Datenstrukturen]]

* [[Unveränderliche Objekte oder Immutable Objects]]
* [[Builder Pattern]]
* [[Singleton (Pattern)]]
* [[OAuth]]
* [[Datenstrukturen]]

```
public class Soyjak {
	private final String name;
	private final String lastname;
	private final int age;
	
	private Soyjak(SoyjakBuilder soyjakBuilder) {
		this.name = soyjakBuilder.name;
		this.lastname = soyjakBuilder.lastname;
		this.age = soyjakBuilder.age;
	}
	
	public static class SoyjakBuilder {
		private final String name;
		private final String lastname;
		private int age;
		
		public SoyjakBuilder(String name, String lastname) {
			this.name = name;
			this.lastname = lastname;
			age = 0;
		}
		
		public SoyjakBuilder age(int age) {
			this.age = age;
			return this;
		}
		
		public Soyjak build() {
			return new Soyjak(this);
		}
	}
}
```

```
public class Skid {
	private static Skid instance;
	
	private Skid() {}
	
	public static synchronized Skid getInstance() {
		if(instance == null) {
			instance = new Skid();
		}
		
		return instance;
	}
	
	public int getValue() {
		return 0;
	}
}
```
