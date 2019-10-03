---
template: post
title: BufferedReader vs Scanner
slug: /bufferedreader-vs-scanner
draft: false
date: 2019-10-03T07:16:03.520Z
description: >-
  BufferedReader, Scanner, Command Arguments are the different ways to provide
  input to a program generally ( java discussed here). Understanding which of
  these to use, knowing what they do behind the curtains is important for every
  developer. 
category: java notes
tags:
  - java notes
---
Before understanding the differences between BufferedReader and Scanner, let's go through some basics:

A _stream_ can be defined as a sequence of data. There are two kinds of Streams − 

* **InputStream** − The InputStream is used to read data from a source.
* **OutPutStream** − The OutputStream is used for writing data to a destination.

Now there are different kinds of streams,  

* **Byte streams** : A byte stream reads bytes of data from an input such as a text or audio file. Byte streams descend from InputStream or OutputStream.
* **Character streams**: Byte streams are generally too low level to use in isolation. Character streams are wrappers for byte streams. Character streams use byte streams to handle I/O with the added benefit of character encoding. Character streams descend from Reader or Writer. FileReader and FileWriter are examples of character streams.
* **Buffered streams**: Byte streams and character streams are unbuffered I/O. This means they rely on the underlying OS to read/write a byte at a time. This is inefficient because reading/writing a single byte from disk is a lot slower than using memory.
  Buffered streams read/write x number of bytes at a time to a memory area called a buffer. Only when the buffer is empty do buffered streams utilize the native input API.
  BufferedReader and BufferedWriter are examples of buffered character streams. BufferedInputStream and BufferedOutputStream are examples of buffered byte streams.
