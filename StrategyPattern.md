# Strategy Pattern

### Definition

A software design pattern in which an algorithm's behavior can be selected at runtime.

### UML

![](http://www.oodesign.com/images/design_patterns/behavioral/strategy_implementation_-_uml_class_diagram.gif)

### Code

```java
	/** The Strategies **/
	public interface Strategy {
		public int foo();
	}
	
	public class ConcreteStrategyA implements Strategy {
		public void foo() {}
	}
	
	public class ConcreteStrategyB implements Strategy {
		public void foo() {}
	}
	
	/** The Context **/
	public class Context {
		private Strategy strategy;
		
		public Context(Strategy strategy) {
			this.strategy = strategy;
		}
		
		public void doFoo() {
			this.strategy.foo();
		}
	}
```

### Links

* http://www.oodesign.com/strategy-pattern.html