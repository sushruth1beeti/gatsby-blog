---
template: post
title: What Is Java Messaging Service
slug: /jms
draft: true
date: 2019-10-01T04:55:00.000Z
description: >-
  Java Message Service (JMS) API, a Java API that allows applications to create,
  send, receive, and read messages using reliable, asynchronous, loosely coupled
  communication. It is very useful in the distributed systems architecture,
  where applications need to talk to each other. 
category: java notes
tags:
  - jms
---
## Messaging

Messaging enables distributed communication that is loosely coupled. A component sends a message to a destination, and the recipient can retrieve the message from the destination. However, the sender and the receiver do not have to be available at the same time in order to communicate. In fact, the sender does not need to know anything about the receiver; nor does the receiver need to know anything about the sender. The sender and the receiver need to know only which message format and which destination to use. In this respect, messaging differs from tightly coupled technologies, such as Remote Method Invocation (RMI), which require an application to know a remote application’s methods.

## JMS API Architecture

A JMS provider is a messaging system that implements the JMS interfaces and provides administrative and control features.

JMS clients are the programs or components, written in the Java programming language, that produce and consume messages. Any Java EE application component can act as a JMS client. Messages are the objects that communicate information between JMS clients. Administered objects are preconfigured JMS objects created by an administrator for the use of clients. The two kinds of JMS administered objects are destinations and connection factories, described in JMS Administered Objects.

![jms-architecture](/media/jms-architecture.gif "jms-architecture")

## Messaging Domains:

A jms provider can provide any or both of these messaging domains:

* Point To Point Messaging (PTP)
* Publisher Subscriber Messaging (Pub/Sub)

A **point-to-point** (PTP) product or application is built on the concept of message queues, senders, and receivers. Each message is addressed to a specific queue, and receiving clients extract messages from the queues established to hold their messages. Queues retain all messages sent to them until the messages are consumed or expire.

Characteristics Of PTP Messaging:

1. Each message has only one consumer.
2. A sender and a receiver of a message have no timing dependencies. The receiver can fetch the message whether or not it was running when the client sent the message.
3. The receiver acknowledges the successful processing of a message.

![PTP](/media/jms-pointtopoint.gif "PTP Messaging")
