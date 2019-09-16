---
template: post
title: What The Hell Are Design Patterns? And Why I Need Them?
slug: /posts/design-patterns-intro
draft: false
date: 2019-09-15T06:28:08.278Z
description: >
  We all look for patterns every day knowingly or not because pattern
  recognition is the basic mechanism by which our brains function. Design
  Patterns in Software Development are no different.
category: 'Design Patterns '
tags:
  - Design Patterns
  - GOF
---
Recognizing patterns allow us to predict and expect what is coming and this is what helped us survive and evolve through time. One of our biggest traits. Design Patterns in Software Development are no different, those are the patterns observed as a part of designing reusable object-oriented software.

![Rabbit](/media/rabbit.jpg "What do you see? Rabbit?")

> Each pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice - Christopher Alexander

Let's say you're the manager of the famous circus in your town. And you want to provide  pre-booking to your show, how are you going to solve this problem?

_TICKETS!!_ You can give all your audience tickets after pre-booking, which they can use as entry on the day of the show. Well, this example is quiet obvious, this solution has existed forever. Whenever there is a question of pre-payment for a service that would be offered in the future, you can use ticketing as a solution. _There is a common occurrence in the question which becomes a pattern and a pre-existing solution which can be reused according to the context._ This becomes very useful in software development, to record experience, observe patterns in designing object-oriented software.

## Definition:

Design patterns make it easier to reuse successful designs and architectures. Expressing proven techniques as design patterns makes them more accessible to developers of new systems. Design patterns help you choose design alternatives that make a system reusable and avoid alternatives that compromise reusability. _Put simply, design patterns help a designer get a design "right" faster._

_In Software terms, design patterns are descriptions of communicating objects and classes that are customized to solve a general design problem in a particular context._

![Steel Structure](/media/structure.jpg "Elements Of A Pattern")

## Elements In A Design Pattern:

* **Pattern Name:** Naming a pattern is very important, it gives us the higher-level abstraction of what the pattern is about. It makes it easier to think about designs and to communicate them and their trade-offs to others. Finding good names is equally hard.
* **Problem:** The problem describes when to apply the pattern. It explains the problem and its context. It might describe specific design problems such as how to represent algorithms as objects.
* **Solution:** The solution describes the elements that make up the design, their relationships, responsibilities, and collaborations. The solution doesn't describe a particular concrete design or implementation, because a pattern is like a template that can be applied in many different situations. So the solution needs to fine tuned according to the domain you're working on.
* **Consequences:** The consequences are the results and trade-offs of applying the pattern. They are critical for evaluating design alternatives and for understanding the costs and benefits of applying the pattern. The consequences for software often concern space and time trade-offs.

## Types Of Design Patterns:

According to the Gang Of Four (the four authors who wrote about design patterns in software development) design patterns can be broadly divided into three categories under the criteria of _purpose_:

* **Creational Patterns:** Creational patterns concern the process of object creation, according to the situation, creation of objects may need more sophisticated way of creation process.
* **Structural Patterns:** Structural patterns deal with the composition of classes or objects, sometimes we may require objects and classes arranged into a structure or hierarchy, that ease the way to realise relationships between objects or classes.
* **Behavorial Patterns:** Behavioral patterns characterize the ways in which classes or objects interact and distribute responsibility. These patterns sets the medium of communication between objects.

Another way of categorization of design patterns is through the criteria of _scope_: scope specifies whether the pattern applies primarily to classes or to objects. The following clearly explains the categorization of design patterns by scope.

![Scope In Design Patterns](/media/design-_pattern_scope.gif "Scope In Design Patterns")

This is all, in the introduction of design patterns, next stop we will discuss more about each design pattern in detail.

Here are the quick references about the topics mentioned:

<https://www.amazon.in/Design-Patterns-Object-Oriented-Addison-Wesley-Professional-ebook/dp/B000SEIBB8>

<https://www.amazon.in/First-Design-Patterns-Brain-Friendly/dp/0596007124>

<https://sourcemaking.com/design_patterns/>
