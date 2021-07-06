---
template: post
title: Introduction to JAVA and Programming Basics
slug: /intro-java
draft: false
date: 2021-07-06T17:01:45.949Z
description: >-
  In this post, I write about Introduction to JAVA and touch upon the basics of
  programming.
category: 'JAVA,OOP'
tags:
  - java
  - oop
---
**Your traditional definition of Java**: Java is a high-level programming language originally developed by Sun Microsystems and released in 1995. Java runs on a variety of platforms, such as Windows, Mac OS, and the various versions of UNIX.

I worked with java first during my intial days at work. We had to write APIs in SpringBoot and SpringMVC frameworks which were written in Java. Java is an objected oriented programming langauge (It is a programming paradigm where a program design is thought of in terms of objects). Well, not purely object-oriented of course. For any language to qualify as a purely object-oriented language it needs to pass 7 qualities:

* Encapsulation/Data Hiding
* Inheritance
* Polymorphism
* Abstraction
* All predefined types are objects
* All user-defined types are objects
* All operations performed on objects must be only through methods exposed at the objects.

Java doesn't qualify point 5 and 7. But we will discuss more on that.

Java is multi-threaded, platform-independent, architecture-neutral, and can be extended to satisfy object model.

When we consider a Java program, it can be defined as a collection of objects that communicate via invoking each other's methods.



* **Object** − Objects have states and behaviors. Example: A dog has states - color, name, breed as well as behavior such as wagging their tail, barking, eating. An object is an instance of a class.
* **Class** − A class can be defined as a template/blueprint that describes the behavior/state that the object of its type supports.
* **Methods** − A method is basically a behavior. A class can contain many methods. It is in methods where the logics are written, data is manipulated and all the actions are executed.
* **Instance Variables** − Each object has its unique set of instance variables. An object's state is created by the values assigned to these instance variables.

## **Java Identifiers**

All Java components require names. Names used for classes, variables, and methods are called identifiers. In Java, there are several points to remember about identifiers. They are as follows −



* All identifiers should begin with a letter (A to Z or a to z), currency character ($), or an underscore (_).
* After the first character, identifiers can have any combination of characters.
* A key word cannot be used as an identifier.
* Most importantly, identifiers are case sensitive.
* Examples of legal identifiers: age, $salary, _value, __1_value.
* Examples of illegal identifiers: 123abc, -salary.



## Java Modifiers

Like other languages, it is possible to modify classes, methods, etc., by using modifiers. There are two categories of modifiers −



* Access Modifiers − default, public, protected, private
* Non-access Modifiers − final, abstract, strictfp



We will be looking into more details about modifiers in the next section.



## Java Variables

Following are the types of variables in Java −



* Local Variables
* Class Variables (Static Variables)
* Instance Variables (Non-static Variables)
* Java Arrays

Arrays are objects that store multiple variables of the same type. However, an array itself is an object on the heap. We will look into how to declare, construct, and initialize in the upcoming chapters.



## Java Enums

Enums were introduced in Java 5.0. Enums restrict a variable to have one of only a few predefined values. The values in this enumerated list are called enums.



With the use of enums, it is possible to reduce the number of bugs in your code.
