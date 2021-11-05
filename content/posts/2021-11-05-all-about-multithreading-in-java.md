---
template: post
title: All about multithreading in java
slug: /multithreading-in-java
draft: false
date: 2021-11-04T23:32:34.839Z
description: 'In this post, I write about multithreading in java'
category: java
tags:
  - java
---
## Why multithreading?

Generally to achieve concurrent executions, there are two ways using multi-process environment or multi-threaded environment. Java uses multi-threading to achieve concurrent programming. It effectively uses less memory and shares resources that is common with the process but in order create problematic communication between threads.

Multithreading makes for the maximum utilization of the CPU by multitasking, by using light weight processes within the process called threads. This is the standard definition you see everywhere on the internet. But when do you really need multithreading? Does multithreading really run multiple threads at the same time? Let's say I have a single core machine, I know I can run only a single thread at any time. How does the multithreading work in this case? How does the multithreading work when we have multiple core machine?

## Multithreading in java

In java, multithreading can be achieved using **Thread class or Runnable interface**. Thread class extends Runnable interface which has a single abstract method called _run()_, which the Thread class implements.

Runnable Interface source code:

```
@FunctionalInterface
public interface Runnable {
    /**
     * When an object implementing interface {@code Runnable} is used
     * to create a thread, starting the thread causes the object's
     * {@code run} method to be called in that separately executing
     * thread.
     * <p>
     * The general contract of the method {@code run} is that it may
     * take any action whatsoever.
     *
     * @see     java.lang.Thread#run()
     */
    public abstract void run();
}
```

Thread class source code (important methods listed):

```
public class Thread {

        // there also exists different overloaded constructor to create Thread object
        // refer to javadoc for the complete source code

        public void run() {
           if(this.target != null) target.run();
        }

	public synchronized void start() {
		/**
		 * * This method is not invoked for the main method thread or "system" * group
		 * threads created/set up by the VM. Any new functionality added * to this
		 * method in the future may have to also be added to the VM. * * A zero status
		 * value corresponds to state "NEW".
		 */
		if (threadStatus != 0)
			throw new IllegalThreadStateException();
		/*
		 * Notify the group that this thread is about to be started * so that it can be
		 * added to the group's list of threads * and the group's unstarted count can be
		 * decremented.
		 */ group.add(this);
		boolean started = false;
		try {
			start0();
			started = true;
		} finally {
			try {
				if (!started) {
					group.threadStartFailed(this);
				}
			} catch (Throwable ignore) {
				/*
				 * do nothing. If start0 threw a Throwable then it will be passed up the call
				 * stack
				 */ }
		}
	}

	private native void start0();
}
```

There are two ways in which you can leverage multithreading in java:

1. Extending thread class and overriding the run method
2. Implementing the runnable interface and implementing the run method. Later creating the object of the class and pass it as a parameter to the Thread object.

**Which one's to use when?**

You extend Thread class when you want to change or override methods from the Thread class, you can choose to extend the Thread class when you want modify any default behavior of the Thread class.

You implement runnable interface when there is already a class extending your class, or you just want to create a thread without wanting to change any default behavior of the thread class.

Examples using threads in different ways:

```
// extending Thread class

class Y extends Thread {

	@Override
	public void run() {
		// TODO Auto-generated method stub
		System.out.println("in run method");
	}

	public static void main(String[] args) {
		Y y = new Y();
		y.start();
	}

}

// implementing Runnable interface

class Y implements Runnable {

	@Override
	public void run() {
		// TODO Auto-generated method stub
		System.out.println("in run method");
	}

	public static void main(String[] args) {
		Y y = new Y();
		Thread t = new Thread(y);
		t.start();
	}

}
```

## How a thread is created?

As we have discussed, we can leverage multithreading in two ways as above. By extending thread class, whenever we do _t.start() (from above example),_ the start method in the Thread class is called, which in turn calls the start0() native method which has code in the c/c++. After creating a new thread, it executes the overrided run() method in you class.

Similar thing happens when the class implements Runnable interface, you pass the object of your class to the Thread class constructor. It executes a parameterized constructor with target as parameter. But this time when the start0 method calls the run method, run method of the target object gets called. 

Go through the source code to wrap your head around this concept if the explanation above was unclear.
