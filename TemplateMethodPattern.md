# Template Method Pattern

### Definition

A behavioral design pattern that defines the program skeleton of an algorithm in a method, deferring some steps to subclasses.

### UML

![](http://www.oodesign.com/images/design_patterns/behavioral/template_method_implementation_-_uml_class_diagram.gif)

### Code

```java
	/** The Abstract class **/
	public abstract class AbstractClass {
	
		public final void templateMethod() {
			primitiveOperationA();
			primitiveOperationB();
			concreteOperation();
			hook();
		}
		
		public abstract void primitiveOperationA();
	
		public abstract void primitiveOperationB();
	
		public void concreteOperation() {
			// some implementation here
		}
		
		public void hook() {}	// a concrete method that does nothing!
	}
	
	/** The Concrete class **/
	public class ConcreteClass extends AbstractClass {
	
		@Override
		public void primitiveOperationA() {}
		
		@Override
		public void primitiveOperationB() {}
		
		@Override
		public void hook() {
			// do something special here
		}
	}
```

### Links

* http://www.oodesign.com/template-method-pattern.html