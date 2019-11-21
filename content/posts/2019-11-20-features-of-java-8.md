---
template: post
title: Features Of Java 8
slug: /java-8-features
draft: false
date: 2019-11-20T09:51:21.356Z
description: >-
  Java 8 introduces new features such as lambda expressions, forEach iterables,
  default and static methods for interfaces etc, this notes will discuss each of
  it for better understanding.
category: java notes
tags:
  - java notes
---
## Java Interface Changes: default, static methods

**Default:**

Before Java 8, interfaces didn't support method implementations, we only used to write the method signatures, all the classes implementing the classes must implement this method or we need to change the class to abstract.

Imagine there is an old interface, written long back, and there are many classes implementing this interface, if we were to change this interface by adding a new method, we will need to implement this  method in all those inheriting classes. With this new feature, we can implement a method in the interface by using the keyword default in the method signature, this makes the implementation for the inheriting classes not necessary.

But giving the feature of default method for interfaces, recreates "diamond problem" in java, which is the inheriting class doesn't know from where to inherit the default method in case of multiple interfaces have the same default method. To solve this problem, whenever the compiler can't decide the default method, you will need to override the default method and provide your own implementation.

Important Points:

* Java interface default methods will help us in extending interfaces without having the fear of breaking implementation classes.
* Java interface default methods has bridge down the differences between interfaces and abstract classes.
* Java 8 interface default methods will help us in avoiding utility classes, such as all the Collections class method can be provided in the interfaces itself.
* Java interface default methods will help us in removing base implementation classes, we can provide default implementation and the implementation classes can chose which one to override.
* One of the major reason for introducing default methods in interfaces is to enhance the Collections API in Java 8 to support lambda expressions.
* If any class in the hierarchy has a method with same signature, then default methods become irrelevant. A default method cannot override a method from java.lang.Object. The reasoning is very simple, it’s because Object is the base class for all the java classes. So even if we have Object class methods defined as default methods in interfaces, it will be useless because Object class method will always be used. That’s why to avoid confusion, we can’t have default methods that are overriding Object class methods.
* Java interface default methods are also referred to as Defender Methods or Virtual extension methods.

**Static:**

Static Method works similar to default method except we cannot override them. his feature helps us in avoiding undesired results in case of poor implementation in implementation classes.

Important points:

* Java interface static method is part of interface, we can’t use it for implementation class objects.
* Java interface static methods are good for providing utility methods, for example null check, collection sorting etc.
* Java interface static method helps us in providing security by not allowing implementation classes to override them.
* We can’t define interface static method for Object class methods, we will get compiler error as “This static method cannot hide the instance method from Object”. This is because it’s not allowed in java, since Object is the base class for all the classes and we can’t have one class level static method and another instance method with same signature.
* We can use java interface static methods to remove utility classes such as Collections and move all of it’s static methods to the corresponding interface, that would be easy to find and use.

## Functional Interfaces And Lambda Functions:

**Functional Interface:**

A new annotation @FunctionalInterface has been introduced to mark an interface as Functional Interface. @FunctionalInterface annotation is a facility to avoid accidental addition of abstract methods in the functional interfaces. It’s optional but good practice to use it.

Functional interfaces are long awaited and much sought out feature of Java 8 because it enables us to use lambda expressions to instantiate them. A new package java.util.function with bunch of functional interfaces are added to provide target types for lambda expressions and method references.

Since functional interfaces have only one abstract method, it is easier to work with lambda expressions, we only need to work with arguments and business logic, and can eliminate instantiating class object, and invoking method.

Without lambda expressions:

`Runnable r = new Runnable(){`

`@Override`

`public void run() {`

`System.out.println("My Runnable");`

`}};`

With lambda expressions:

`Runnable r = () -> {System.out.println("My Runnable");};`



# Java Stream API

This is one of the best features according to me in Java 8. It becomes so much easier to work with collections with stream api. Collection interface has been extended with stream() and parallelStream() default methods to get the Stream for sequential and parallel execution.  We can use map/filter/reduce function along side stream, and lambda functions work very well these.

Unlike traditional collections, stream doesn't store data in memory, it works on-demand, it operates on the source data structure (collection and array) and produce pipelined data that we can use and perform specific operations. Such as we can create a stream from the list and filter it based on a condition.

- - -
