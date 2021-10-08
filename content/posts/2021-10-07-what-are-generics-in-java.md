---
template: post
title: What are generics in Java?
slug: /generics
draft: true
date: 2021-10-07T23:37:55.375Z
description: 'In this blog, we learn about generics in java and why we need to use them.'
category: java
tags:
  - java
---
The primary use to introduce generics in java is for type safety. What do I mean by "type safety"? Before generics, if I wanted to store an object type in a list of strings I could do it. I only need to typecast it back to string whenever I want to access it as a string. The problem with this is that,  I could also store an Integer in the list of strings by upcasting it to object. To counter this, generics was introduced as it will force you to determine what type of objects you want to use before runtime.

_**Without Generics:**_

```
        List l = new ArrayList();
```

```
        Object o1 = new String("abc");
```

```
        Object o2 = new Integer(1);
```

```
        l.add(o1);
```

```
        l.add(o2);
```

```
        String s = (String)l.get(1); // this will give runtime error
```

_**With Generics:**_

```
        List<Integer> l = new ArrayList<Integer>();
```

```
        Object o1 = new Integer(1);
```

```
        l.add(o1); // will give compilation error, force you to add Integer type
```

```
        l.add(new Integer(2));
```
