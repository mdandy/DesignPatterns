# Composite Pattern

### Definition

A design pattern that allows you to compose objects into tree structure to represent part-whole hierarchies.

### UML

![](http://www.oodesign.com/images/design_patterns/structural/composite-design-pattern-implementation-uml-class-diagram.png)

### Code

```java
	/** The Component **/
	public interface Component {
		void doOperation();
	}
	
	/** The Component: Leaf **/
	public class Leaf implements Component {
		@Override
		public void doOperation() {}
	}
	
	/** The Component: Composite (Node) **/
	public class Composite implements Component {
		List<Component> components;	
		
		public Composite() {
			this.components = new ArrayList<Component>();
		}

		@Override
		public void doOperation() {
			// doOperation for each Component
			Iterator iter = this.components.iterator();
			while (iter.hasNext()) {
				Component c = iter.next();
				c.doOperation();
			}
		}
		
		public void addComponent(Component component) {
			this.components.add(component);
		}
		
		public void removeComponent(Component component) {
			this.components.remove(component);
		}
		
		public Component getComponent(int index) {
			return this.components.get(index);
		}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Component leaf1 = new Leaf();
			Component leaf2 = new Leaf();
			
			Composite allLeaves = new Composite();
			allLeaves.add(leaf1);
			allLeaves.add(leaf2);
			
			allLeaves.doOperation();
		}
	}
```

### Links

* http://www.oodesign.com/composite-pattern.html