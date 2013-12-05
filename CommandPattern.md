# Command Pattern

### Definition

A behavioral design pattern in which an object is used to represent and encapsulate all the information needed to call a method at a later time.

### UML

![](http://www.oodesign.com/images/design_patterns/behavioral/command_implementation_-_uml_class_diagram.gif)

### Code

```java
	/** The Command **/
	public interface Command {
		public void execute();
	}
	
	public class ConcreteCommand implements Command {
		Receiver receiver;
		
		public ConcreteCommand(Receiver receiver) {
			this.receiver = receiver;
		}

		public void execute() {
			this.receiver.action();
		}
	}
	
	/** The Receiver **/
	public class Receiver {
		public void action() {}
	}
	
	/** The Invoker **/
	public class Invoker {
		Command command;
		
		public Invoker() {}
		
		public void setCommand(Command command) {
			this.command = command;
		}
		
		public void invoke() {
			this.command.execute();
		}
	}
	
	/** The Client **/
	public class MyApp {
		public static void main(String[] args) {
			Invoker invoker = new Invoker();
			Receiver receiver = new Receiver();
			Command command = new ConcreteCommand(receiver);
			
			invoker.setCommand(command);
			invoker.invoke();
		}
	}
```

### Links

* http://www.oodesign.com/command-pattern.html