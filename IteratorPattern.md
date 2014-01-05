# Iterator Pattern

### Definition

A design pattern in which an iterator is used to traverse a container and access the container's elements.

### UML

![](http://www.oodesign.com/images/design_patterns/behavioral/iterator_implementation_-_uml_class_diagram.gif)

### Code

```java
	/** The Iterator **/
	public interface Iterator {
		Object next();
		void remove();
		boolean hasNext();
	}
	
	public class ConcreteIterator implements Iterator {
		Object[] arr;
		int index = 0;
		
		public ConcreteIterator(Object[] arr) {
			this.arr = arr;
		}
		
		@Override
		public Object next() { 
			return arr[index++];
		}
		
		@Override
		public void remove() {
			throw new UnsupportedOperationException("Not supported");
		}
		
		@Override
		public boolean hasNext() {
			return index < arr.length;
		}
	}
	
	/** The Aggregate **/
	public interface Aggregate {
		Iterator createIterator();
	}
	
	public class ConcreteAggregate implements Aggregate {
		Object[] arr = {new Object(), new Object(), new Object()};
		
		@Override
		public Iterator createIterator() {
			return new ConcreteIterator(arr);
		}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Aggregate agg = new ConcreteAggregate();
			Iterator iter = agg.createIterator();
			
			while (iter.hasNext()) {
				Object o = iter.next();
				o.toString();
			}
		}
	}
```

### Links

* http://www.oodesign.com/iterator-pattern.html