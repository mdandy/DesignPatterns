# Facade Pattern

### Definition

A facade is an object that provides a simplified interface to a larger body of code, such as a class library. A facade can:
* make a software library easier to use, understand and test, since the facade has convenient methods for common tasks
* make the library more readable, for the same reason
* reduce dependencies of outside code on the inner workings of a library, since most code uses the facade, thus allowing more flexibility in developing the system
* wrap a poorly designed collection of APIs with a single well-designed API (as per task needs).

### UML

![](https://upload.wikimedia.org/wikipedia/commons/a/ac/FacadeDesignPattern.png)

### Code

```java
	/** The Subsystem classes **/
	public class Subsystem1 {
		public void foo() {}
	}
	
	public class Subsystem2 {
		public void bar() {}
	}
	
	/** The Facade **/
	public class Facade {
		Subsystem1 s1;
		Subsystem2 s2;
		
		public Facade(Subsystem1 s1, Subsystem2 s2) {
			this.s1 = s1;
			this.s2 = s2;
		}

		public void doSomething() {
			s1.foo();
			s2.bar();
		}
	}
```

### Links

* https://en.wikipedia.org/wiki/Facade_pattern