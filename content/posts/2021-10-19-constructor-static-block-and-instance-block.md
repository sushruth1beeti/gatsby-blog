---
template: post
title: 'Constructor, Static block and instance block'
slug: /order-of-execution
draft: false
date: 2021-10-19T18:51:02.871Z
description: >-
  In this blog, we are going to learn about the order of executions of
  constructor, static block and instance block.
category: java notes
tags:
  - Java notes
---
## Constructor:

A constructor in Java is a block of code similar to a method that's called when an instance of an object is created. A constructor doesn't have a return type. The name of the constructor must be the same as the name of the class. Unlike methods, constructors are not considered members of a class. This is the standard definition of constructor lifted from java docs.

Main use of constructor is to instantiate class variable or run pre-object creation logic. Example of the constructors given below.

```
class Human {
  private String name;
  private int age;
  public Human() {
    this.name = name;
    this.age = age;
  }
}
```

In this blog, we are only going to cover the order of execution of constructor, static block and instance block. So I'm not going to write in detail about the constructor. Save that up for a later blog maybe.

## Static block:

Static block is a block of code run during the class load. It is mainly used to setup/initialise variables or run the code that has to happen before the object creation. It is very similar to constructor in terms of functionality but differs in one thing, it only runs once during the class load time.

Example given below:

```
class G {

  public G ()	{
	System.out.println("in G constructor");
  }

  // static block

  static {
	System.out.println("G:Static 1");
  }

}
```

## Instance block:

Some times called Instance Initializing block, Instance block is a non static block used to initialise the variables at runtime or run a logic before the object creation. The difference between instance block and static block in a class is that instance block will run everytime the class is instantiated. It runs after the constructor call is made and right after the child constructor calls the parent constructor (super();).

Example given below:

```
class G {

  public G ()	{
	System.out.println("in G constructor");
  }

  // non static block
  
  {
	System.out.println("G: Non Static 1");
  }
```

## Order of execution in the class:

Follow this example and try to guess the output of the program:

```
class G {

	{
		System.out.println("G non static block");
	}

	public G() {
		System.out.println("in G constructor");
	}

	static {
		System.out.println("G:Static 1");
	}

	static {
		System.out.println("G: Static 2");
	}

}

class C extends G {
	{
		System.out.println("C non static block");
	}

	public C() {
		System.out.println("in C constructor");
	}

	static {
		System.out.println("C:Static 1");
	}

	static {
		System.out.println("C: Static 2");
	}

	public static void main(String args[]) {
		System.out.println("new C()     " + new C());
		System.out.println("new G()    " + new G());
	}
}
```

1. Entry point of the this program is main method in class C. In order to do that class C will be loaded but class C extends class G hence class G is loaded first.
2. After class G is loaded both the static blocks in class will be printed.
3. Then class C is loaded both the static blocks in class will be printed.
4. Then main method is called in class C will be called which will in turn print new C().
5. Constructor in C is called, the first line in constructor C is super(); which will call the constructor in G.
6. Constructor in G will call it's super class constructor which here in this example is object class. Then the instance blocks in class G are executed.
7. After which, constructor in G will finish executing and pass the control back to it's child constructor. It will execute the child's instance blocks now. And later finish the executing remaining of constructor's code.
8. After which it will print the first line in the main method.
9. Follow the same steps for the next line of the of the main method and try to come up with an answer. But remember static blocks are not executed this time. 



Solution:

```
OUTPUT: 

_G:Static 1_

_G: Static 2_

_C:Static 1_

_C: Static 2_

_G non static block_

_in G constructor_

_C non static block_

_in C constructor_

_new C()     C@442d9b6e_

_G non static block_

_in G constructor_

_new G()    G@ee7d9f1_
```
