<a name="toc"/>
# Table of Contents

* [Singleton Pattern](#singleton)
* [Single Threading Singleton Pattern](#single)
* [Multi Threading Singleton Pattern](#multi)
* [Enum Instance Pattern](#enum)

-----

<a name="singleton"></a>
# Singleton Pattern

### Definition

A design pattern that restricts the Instantiation of a class to one object. 

### UML

![](http://www.oodesign.com/images/design_patterns/creational/singleton_implementation_-_uml_class_diagram.gif)

### Links

* http://www.oodesign.com/singleton-pattern.html

[&uarr; back to top](#toc)

-----

<a name="single"></a>
# Single Threading Singleton Pattern

### Code

```java
	public class Singleton {
		private static Singleton instance;
		
		private Singleton() {}
		
		public static Singleton getInstance() {
			if (instance == null) {
				instance = new Singleton();
			}
			return instance;
		}
		
		public void foo() {}
	}
```

[&uarr; back to top](#toc)

-----

<a name="multi"></a>
# Multi Threading Singleton Pattern

### Definition

**Lazy instantiation using double-checked locking mechanism:** A software design pattern used to reduce the overhead of acquiring a lock by first testing the locking criterion (the "lock hint") without actually acquiring the lock. Only if the locking criterion check indicates that locking is required does the actual locking logic proceed.

### Code

```java
	public class Singleton {
		private static volatile Singleton instance;
		
		private Singleton() {}
		
		public static Singleton getInstance() {
			if (instance == null) {
				synchronized (Singleton.class) {
					if (instance == null) {	
						instance = new Singleton();
					}
				}
			}
			return instance;
		}
		
		public void foo() {}
	}
```

[&uarr; back to top](#toc)

-----

<a name="enum"></a>
# Enum Instance Pattern

### Definition

Enum, as written in javadocs, provides an implicit support for thread safety and only one instance is guaranteed. 

### Code

```java
	public enum Singleton {
		INSTANCE;

		public void foo() {}
	}
```

[&uarr; back to top](#toc)
