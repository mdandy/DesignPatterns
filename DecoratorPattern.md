# Decorator Pattern

### Definition

A software design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.

### UML

![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Decorator_UML_class_diagram.svg/400px-Decorator_UML_class_diagram.svg.png)

### Code

```java
	/** The Component **/
	public abstract class Beverage {
		public abstract double cost();
	}
	
	/** The Concrete Components **/
	public class Expresso extends Beverage {
		@Override
		public double cost() { return 3.49; }
	}
	
	public class Decaf extends Beverage {
		@Override
		public double cost() { return 2.99; }
	}
	
	/** The Decorator **/
	public abstract class CondimentDecorator extends Beverage {
		protected Beverage beverage;	

		public CondimentDecorator(Beverage beverage) {
			this.beverage = beverage;
		}
	}
	
	/** The Concrete Decorators **/
	public class Milk extends CondimentDecorator {
		public Milk(Beverage beverage) {
			super(beverage);
		}	

		@Override
		public double cost() {
			return 0.25 + beverage.cost();
		}
	}
	
	public class Whip extends CondimentDecorator {
		public Whip(Beverage beverage) {
			super(beverage);
		}
		
		@Override
		public double cost() {
			return 0.20 + beverage.cost();
		}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Beverage beverage = new Espresso();
			beverage = new Milk(beverage);
			beverage = new Milk(beverage);	// extra milk
			beverage = new Whip(beverage);
			System.out.println("$" + beverage.cost());
		}
	}
```

### Links

* http://www.oodesign.com/decorator-pattern.html