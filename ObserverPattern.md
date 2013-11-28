# Observer Pattern

### Definition

A software design pattern in which an object, called the subject (or observable), maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods. It is mainly used to implement distributed event handling systems.

**Observable/Subject:** Objects use this interface (or abstract class) to register as observers and also to remove themselves from being observers.

**Observer:** All potential observers need to implement the Observer interface (or abstract class). This interface just has one method, `update()`, that gets called when the Subject's state changes.

Can be done in two flavors: **push** and **pull** communication.

**Push model:** The subjects send detailed information about the change to the observer whether it uses it or not. 

**Pull model:** The subject just notifies the observers when a change in his state appears and it's the responsibility of each observer to pull the required data from the subject.


Java has built-in interface for this pattern: `java.util.Observer` and `java.util.Observable`.

### UML

![](http://www.oodesign.com/images/design_patterns/behavioral/observer_implementation_-_uml_class_diagram.gif)

### Code

```java
	/** The Observable/Subject **/
	public class EventSource extends Observable {
		public void foo() {
			setChanged();	// needed in order to trigger notification
			notifyObservers();
		}
	}
	
	/** The Observers **/
	public class EventHandlerA implements Observer {
		@Override
		public void update(Observable o, Object arg) {}
	}
	
	public class EventHandlerB implements Observer {
		@Override
		public void update(Observable o, Object arg) {}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Observable eventSource = new EventSource();
			Observer eventHandlerA = new EventHandlerA();
			Observer eventHandlerB = new EventHandlerB();
			
			// subscribe
			eventSource.addObserver(eventHandlerA);
			eventSource.addObserver(eventHandlerB);
			
			// notify
			eventSource.foo();
		}
	}
```

### Links

* http://www.oodesign.com/observer-pattern.html