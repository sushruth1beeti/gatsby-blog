---
template: post
title: Nested Classes in Java
slug: /nested-classes
draft: false
date: 2021-10-18T15:44:37.639Z
description: >-
  Java programming language allows you to declare a class inside another class.
  We see how and why we need to use inner classes in our code.
category: java notes
tags:
  - java notes
---
## Why Nested Classes?

Nested classes allows developers to declare a class inside a class. We could obviously write nested class as a separate class from the outer class. But it makes more sense to write a few classes as nested classes in certain scenarios:

* When the class you want write is a logical component of outer class and outer class only. That means use this class in the outer class only and no other classes use it.
* For better encapsulation, encapsulating nested classes inside outer classes and making them private (inner classes can still access all the private variables of outer class) provides good design by hiding it from other classes which need not know about it.
* Sometimes it makes the code more readable(I doubt in quite a few cases, with complex nesting classes) and more maintainable.

There are two categories of inner classes: static and non-static. Terminology wise non-static nested classes are called inner classes. 

## Inner Classes:

Inner classes are part of the instance of the outer class just like instance variables and instance methods. Inner classes can access all variables and methods of it's enclosing class. Because inner classes are part of the instance of the outer class it cannot define any static member. This statement is only true for java versions earlier than 16. Starting form 16, java supports static methods inside inner class, below is an example.

```
class A {
   class B {
     static void print() {
       System.out.println("Static method called");
     } 
     void instanceMethod() {
      System.out.println("Instance method called");
     }
   }
  public static void main(String[] args) {
    A.B.print();
  }
}
```

Calling an instance method of the inner class looks like this:

```
A outerObject = new A();
A.B innerObject = outerObject.new B();
innerObject.instanceMethod();
```

## Static Nested Classes:

Static Nested classes are nested classes where the class modifier is static. It is associated with the outer class. It cannot directly access the outer class non-static members.

Below is an example for static nested class:

```
public class A {
	String foo;
	static String staticFoo = "2";
	public A() {
		foo = "2";
	}
	
	static class B {
		public void print() {
			System.out.println(staticFoo);
			// System.out.println(foo); compilation error
		}
	}

	public static void main(String[] args) {
		A b = new A();
		A.B b2 = new A.B();
		b2.print();
	}
}
```

## Local Classes:

Local classes are a type of inner classes but written inside a method body. According to the java docs definition, local classes are classes that are defined in a block, which is a group of zero or more statements between balanced braces. An example of the local class is given below:

```
public class A {

	public static void someMethod() {
		class B {
			public void someMethodInB() {
				System.out.println("Method in B called");
			}
		}
		B b = new B();
		b.someMethodInB();
	}
	public static void main(String[] args) {
		A.someMethod();
	}
}
```

Quick question: Can local classes be static?
We know we categorised local classes under inner classes which means non-static nested class. But why shouldn't local classes be static. The main purpose for a local class is to access the non-static and static data members of the method or a scope. If it was static it would be restricting the non-static data members.

## Anonymous Classes:

Another subtype of inner classes, anonymous classes are used to make the code concise, by provided a way to declare and instantiate the class at a time. They are like local classes but without name. You can only use them once.

An example of the anonymous classes is given below:

```
public class A {
	int b = 3;
	public static void someMethod() {
		
		interface B {
			void method1();
		}
		
		B b = new B() {
			public static void method2() {
				System.out.println("in static method2");  // no way to access this method
			}

			@Override
			public void method1() {
				// TODO Auto-generated method stub
				
			}
			
		};
		b.method1();
	}
	public static void main(String[] args) {
		A.someMethod();
	}
}
```

## Lambda Expressions:

Lambda expressions provide a way to write the anonymous classes in an even more concise fashion. If the interface contains just one method,syntax of anonymous classes may seem unwieldy and unclear. With lambda expression you can write the similar implementation in a easy way. One example given below:

```
 

public class A {
	int b = 3;
	public static void someMethod() {
		
		interface B {
			void method1();
		}
		
		B b = () -> System.out.println("In method1");
		b.method1();
	}
	public static void main(String[] args) {
		A.someMethod();
	}
}
```

When to use inner classes, static nested classes, anonymous classes and lambda expressions (lifted from java docs):

**Local class**: Use it if you need to create more than one instance of a class, access its constructor, or introduce a new, named type (because, for example, you need to invoke additional methods later).

**Anonymous class:** Use it if you need to declare fields or additional methods.

**Lambda expression:** Use it if you are encapsulating a single unit of behavior that you want to pass to other code. For example, you would use a lambda expression if you want a certain action performed on each element of a collection, when a process is completed, or when a process encounters an error.

Use it if you need a simple instance of a functional interface and none of the preceding criteria apply (for example, you do not need a constructor, a named type, fields, or additional methods).

**Nested class**: Use it if your requirements are similar to those of a local class, you want to make the type more widely available, and you don't require access to local variables or method parameters.

Use a non-static nested class (or inner class) if you require access to an enclosing instance's non-public fields and methods. Use a static nested class if you don't require this access.
