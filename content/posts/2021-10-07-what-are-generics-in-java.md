---
template: post
title: Generics in Java
slug: /generics
draft: false
date: 2021-10-07T23:37:55.375Z
description: 'In this blog, we learn about generics in java and why we need to use them.'
category: java
tags:
  - java
---
## Why?

The main use to introduce generics in java is for type safety. What do I mean by "type safety"? Before generics, if I wanted to store an object type in a list of strings I could do it. I only need to typecast it back to string whenever I want to access it as a string. The problem with this is that,  I could also store an Integer in the list of strings by upcasting it to object. To counter this, generics was introduced as it will force you to determine what type of objects you want to use before runtime.

**_Without Generics:_**

```
        List l = new ArrayList();
        Object o1 = new String("abc");
        Object o2 = new Integer(1);
        l.add(o1);
        l.add(o2);
        String s = (String)l.get(1); // this will give runtime error
```

**_With Generics:_**

```
        List<Integer> l = new ArrayList<Integer>();
        Object o1 = new Integer(1);
        l.add(o1); // will give compilation error, force you to add Integer type
        l.add(new Integer(2));
```

To summarise, generics offer type safety, remove explicitly type casting certain objects you want to use, provides compile time checking.

## How?

Generics enable classes and interfaces to be type parameters when defining classes and methods. Type parameters are different from method parameters, type parameters offer a way to to re-use the same class or a method for different class/interface types.

```
// Generic class definition:  
class name<T1, T2, T3....> {....}
```

There are certain type parameter naming conventions which makes it easier to differentiate between type parameters and other classes/interfaces in the code.

**E -** Element,
**K -** Key,
**N -** Number,
**T -** Type,
**V -** Value

An example of a node class using generics:

```
class Node<T> {
    T value;
    Node<T> next;
    public Node(T value, Node<T> next) {
    	this.value = value;
    	this.next = next;
    }
    
    @Override
    public String toString() {
    	return this.value.toString();
    }
}
```

Check the code below, if you create your node object like this, would you get a compilation error?

```
    Node n = new Node(2, null);
```

The answer is no (you would get some warnings tho). Because generics are backward compatible, meaning the line above would just mean code below, if you write it using generics:

```
    Node<Object> n = new Node<Object>(2, null);
```

## Multiple Type Parameters

We could also have multiple type parameters in java. HashMap is one example for it.

```
class MyHashMap<K, V> {
	public MyHashMap(K key, V value) {
		// constructor
	}
	
	public V getValue(K key) {
		// code to get value
		return null;
	}
}
```

## Generic Methods:

Concept of generic methods is very similar to generic classes, generic methods basically introduce their own type parameter. The scope of these types are limited to the method.

```
public static <T1, T2, T3> boolean compare(Map<T1, T2> p, List<T3> b) {
       // method implementation
}
```

If you were to call the above 'compare' method by creating an object of this class, it would like something like below

```
myObject.<T1, T2, T3>compare(map, list);
```

But you don't have to put the angled brackets every time you invoke a method of the class. The compiler will infer the types that are required. This is called **inference**. This also works with constructors which is called constructor inference.

```
myObject.compare(map, list); // type parameters <T1, T2, T3> are inferred
```

## Bounded Type Parameters:

**Upper bounded** type parameters allows us to restrict the types that can be used as type parameters, example given below. Here "extends" works for both classes and interfaces in a general sense.

```
// example of class signature using upper bounded type parameter
// parameter V must extend T, meaning V is upper bounded by T

class MyHashMap<K, T, V extends T> {}
```

```
// example of method signature using upper bounded type parameter
// parameter T3 must extend T1, meaning T3 is upper bounded by T1
 
public static <T1, T2, T3 extends T1> boolean compare(Map<T1, T2> p, List<T3> b) 
```

You could also have **multiple type parameters** extending a class. But you would still need to follow that classes don't support multiple inheritance that means at max only one class can extend the type parameter and any number of interfaces. And the bounding class needs to written first then the interfaces if any otherwise it leads into a compilation error.

An example (Use '&' to extend to multiple classes and interfaces):

```
public static <T1, T2 extends T3 & T4 & T5> boolean compare(Map<T1, T2>, ....)
```

**Quick Questions:**

If I had asked you what all class types can T3, T4, T5 be? _We know that T3 can be a class or an interface. So either T3, T4, T5 are all interfaces or T3 is class and T4, T5 are interfaces. Any other combination will lead to an compilation error._

Object o = new String("5") is this a valid assignment? _Yes, by inheritance we know that child objects can be upcasted to parent's class reference. Object is a parent for every class hence this is valid._

ArrayList<Object> a = new ArrayList<String>(); is this a valid assignment ? No, we need to observe that ArrayList<Object> is not the parent class for ArrayList<String>. This would be valid: Object a = new ArrayList<String>(); Object is a parent class for ArrayList class.

**Subtyping:** You can subtype an generic class by extending or implementing it. The relationship between the type parameters of one class or interface and the type parameters of another are determined by the extends and implements clauses. An example given below:

```
public class A<T1, T2 extends T3> extends B<T1> {}
```

In the above example you have subtyped class A with B. A<String, Integer extends Number> is a subtype of B<String>.

**Wildcard Types:** The wildcard types (?) are used when you don't want to explicitly specify a type parameter, or for an unknown type. List<?> this is a list of an unknown type. Main use of wildcard is for writing methods or classes which provide common functionality for multiple types. Or when you want to write methods or classes that doesn't depend on a specific type.

**Examples:**

```
// this method prints any list of all types 
public void printList(List<?> list) {// prints list}
```

**Quick Question:**
What is the difference between List<Object> listA and another List<?> listB both initialised? you can add any child class of object to listA, but you can only add null to listB. 

Lower bounded type parameters allows us to restrict the types that can be used as type parameters, it creates the lower bound of classes we can use as type parameters.

```
public void method1(Map<String, ? super Integer> a){}
```

In the example above, ? super Integer is lower bounded by class Integer, so types Number, Object would be valid to pass.

## **Wildcards and subtyping:**

In the above topics, we have discussed that List<String>, List<Object> are not in the same inheritance, meaning they are not child and parent. But using wildcard you could create that inheritance if you wanted. The code would look like this:

```
// taken from javadocs
List<? extends Integer> intList = new ArrayList<>(); 
List<? extends Number>  numList = intList;
```
This works because intList can be any subclass from Integer and below. numList can be any subclass from Number and below. So List<? extends Number> can be thought of as a valid parent class of List<? extends Integer>
```
List<? super Number> numList = new ArrayList<>();
List<? super Integer> intList = numList;
```
The same is true if you use super types instead.
