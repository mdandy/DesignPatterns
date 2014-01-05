# State Pattern

### Definition

A behavioral software design pattern that encapsulates varying behavior for the same routine based on an object's state object. State pattern closely resembles Strategy Pattern.

### UML

![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e8/State_Design_Pattern_UML_Class_Diagram.svg/400px-State_Design_Pattern_UML_Class_Diagram.svg.png)

### Code

```java
	/** The State **/
	public interface State {
		void handle();
	}
	
	public class ConcreteStateA implements State {
		@Override
		public void handle() {}
	}
	
	public class ConcreteStateB implements State {
		@Override
		public void handle() {}
	}
	
	/** The Context **/
	public class Context {
		private State stateA;
		private State stateB;	

		private State currentState;
		
		public Context() {
			this.stateA = new ConcreteStateA();
			this.stateB = new ConcreteStateB();
			this.currentState = this.stateA;
		}
		
		private void setCurrentState(State state) {
			this.currentState = state;
		}
		
		public void request() {
			this.currentState.handle();
			if (this.currentState == this.stateA) {
				setCurrentState(this.stateB);
			} else {
				setCurrentState(this.stateA);
			}
		}
	}
```

### Links

* https://en.wikipedia.org/wiki/State_pattern