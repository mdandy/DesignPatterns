<a name="toc"></a>
# Table of Contents

* [Simple Factory Pattern](#simple)
* [Factory Pattern](#factory)
* [Abstract Factory Pattern](#abstract)

------

<a name="simple"></a>
# Simple Factory Pattern

### Definition

An object-oriented creational design pattern that creates objects without exposing the instantiation logic to the client. It refers to the newly created object through a common interface

### UML

![](http://www.oodesign.com/images/stories/factory%20implementation.gif)

### Code

```java
	/** The Factory **/
	public abstract class Factory {
		public static Product create(String type) {
			if (type.equals("A")) return new ConcreteProductA();
			return new ConcreteProductB();
		}
	}
	
	/** The Products **/
	public interface Product {
		public void foo();
	}
	
	public class ConcreteProductA implements Product {
		@Override
		public void foo() {}
	}
	
	public class ConcreteProductB implements Product {
		@Override
		public void foo() {}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Product product = Factory.create("B");
			product.foo();
		}
	}
```

### Links

* http://www.oodesign.com/factory-pattern.html

[&uarr; back to top](#toc)

-----

<a name="factory"></a>
# Factory Pattern

### Definition

An object-oriented creational design pattern to implement the concept of factories and deals with the problem of creating objects (products) without specifying the exact class of object that will be created. The essence of this pattern is to "Define an interface for creating an object, but let the classes that implement the interface decide which class to instantiate. The Factory method lets a class defer instantiation to subclasses."

### UML

![](http://www.oodesign.com/images/stories/factory%20method%20implementation%20-%20uml%20class%20diagram.gif)

### Code

```java
	/** The Factory **/
	public abstract class Factory {
		protected abstract Product create();
		
		public Product foo() {
			return this.create();
		}
	}
	
	public class ConcreteFactory extends Factory {
		@Override
		public Product create() {
			return new ConcreteProduct();
		}
	}
	
	/** The Product **/
	public interface Product {
		public void bar();
	}
	
	public class ConcreteProduct implements Product {
		@Override
		public void bar() {}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Factory factory = new ConcreteFactory();
			Product product = factory.foo();
			product.bar();
		}
	}
```

### Links

* http://www.oodesign.com/factory-method-pattern.html

[&uarr; back to top](#toc)

-----

<a name="abstract"></a>
# Abstract Factory Pattern

### Definition

An object-oriented creational design pattern that produces objects that follow a general pattern and at runtime this factory is paired with any concrete factory to produce objects that follow the pattern of a certain country. In other words, the Abstract Factory is a super-factory which creates other factories (Factory of factories).

### UML

![](http://www.oodesign.com/images/creational/abstract-factory-pattern.png)

### Code

```java
	/** The Factories **/
	public interface class AbstractFactory {
		public AbstractProductA createProductA();
		public AbstractProductB createProductB();
	}
	
	public class ConcreteFactory1 implements AbstractFactory {
		@Override
		public AbstractProductA createProductA() {
			return new ConcreteProductA1();
		}
		
		@Override
		public AbstractProductB createProductB() {
			return new ConcreteProductB1();
		}
	}
	
	public class ConcreteFactory2 implements AbstractFactory {
		@Override
		public AbstractProductA createProductA() {
			return new ConcreteProductA2();
		}
		
		@Override
		public AbstractProductB createProductB() {
			return new ConcreteProductB2();
		}
	}
	
	/** The Products **/
	public interface AbstractProductA {
		public void foo();
	}
	
	public class ConcreteProductA1 implements AbstractProductA {
		@Override
		public void foo() {}
	}
	
	public class ConcreteProductA2 implements AbstractProductA {
		@Override
		public void foo() {}
	}
	
	public interface AbstractProductB {
		public void bar();
	}
	
	public class ConcreteProductB1 implements AbstractProductB {
		@Override
		public void bar() {}
	}
	
	public class ConcreteProductB2 implements AbstractProductB {
		@Override
		public void bar() {}
	}
	

	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			AbstractFactory abstractFactory = get("1");
			AbstractProductB product = abstractFactory.createProductB();
			product.bar();
		}
		
		public static AbstractFactory get(String type) {
			if (type.equals("A")) return new ConcreteFactory1();
			return new ConcreteFactory2();
		}
	}
```

### Links

* http://www.oodesign.com/abstract-factory-pattern.html

[&uarr; back to top](#toc)