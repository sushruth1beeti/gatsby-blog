---
template: post
title: Nested Classes in Java
slug: /nested-classes
draft: true
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
