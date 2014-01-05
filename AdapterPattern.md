# Adapter Pattern

### Definition

A design pattern that translates one interface for a class into a compatible interface. An adapter allows classes to work together that normally could not because of incompatible interfaces, by providing its interface to clients while using the original interface. The adapter translates calls to its interface into calls to the original interface, and the amount of code necessary to do this is typically small. The adapter is also responsible for transforming data into appropriate forms.

### UML

![](http://www.oodesign.com/images/structural/adapter-pattern.png)

### Code

```java
	/** The Target **/
	public interface Target {
		void foo();
	}
	
	/** The Adaptee **/
	public interface Adaptee {
		void bar();
	}
	
	/** The Adapter **/
	public class Adapter implements Target {
		Adaptee adaptee;
		
		public Adapter(Adaptee adaptee) {
			this.adaptee = adaptee;
		}
		
		@Override
		public void foo() {
			this.adaptee.bar();
		}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Adaptee adaptee = new Adaptee();
			Target targetAdapter = new Adapter(adaptee);
			targetAdapter.foo();
		}
	}
```

### Links

* http://www.oodesign.com/adapter-pattern.html