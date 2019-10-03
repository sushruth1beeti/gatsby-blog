---
template: post
title: BufferedReader vs Scanner
slug: /bufferedreader-vs-scanner
draft: false
date: 2019-10-03T07:16:03.520Z
description: >-
  BufferedReader, Scanner, Command Arguments are the different ways to provide
  input to a program generally. Understanding which of these to use, knowing
  what they do behind the curtains is important for every developer. 
category: java notes
tags:
  - java notes
---
Before understanding the differences between _BufferedReader_ and _Scanner_, let's go through some basics:

A _stream_ can be defined as a sequence of data. There are two kinds of streams:

* **InputStream** − The InputStream is used to read data from a source. InputStream class is the superclass of all the io classes i.e. representing an input stream of bytes. It represents input stream of bytes. Applications that are defining subclass of InputStream must provide method, returning the next byte of input.
  A reset() method is invoked which re-positions the stream to the recently marked position.
* **OutPutStream** − The OutputStream is used for writing data to a destination.This abstract class is the superclass of all classes representing an output stream of bytes. An output stream accepts output bytes and sends them to some sink. Applications that need to define a subclass of OutputStream must always provide at least a method that writes one byte of output.

 There are different kinds of streams:

* **Byte streams** : A byte stream reads bytes of data from an input such as a text or audio file. Byte streams descend from InputStream or OutputStream.
* **Character streams**: Byte streams are generally too low level to use in isolation. Character streams are wrappers for byte streams. Character streams use byte streams to handle I/O with the added benefit of character encoding. Character streams descend from Reader or Writer. FileReader and FileWriter are examples of character streams.
* **Buffered streams**: Byte streams and character streams are unbuffered I/O. This means they rely on the underlying OS to read/write a byte at a time. This is inefficient because reading/writing a single byte from disk is a lot slower than using memory.
  Buffered streams read/write x number of bytes at a time to a memory area called a buffer. Only when the buffer is empty do buffered streams utilize the native input API.
  BufferedReader and BufferedWriter are examples of buffered character streams. BufferedInputStream and BufferedOutputStream are examples of buffered byte streams.

As discussed earlier implementations of reader or writer abstract class defines how the bytes are converted into characters. Here are the most used reader and writer  implementations:

* **InputStreamReader**: The _InputStreamReader_ reads the uninterpreted bytes from the input stream and interprets bytes to characters using a character set. It extends an abstract class Reader. Some other examples of reader class are: _BufferedReader_, _CharArrayReader_, _FilterReader_, _PipedReader_, _StringReader_. 
* **OutputStreamReader**: _OutputStreamWriter_ class connects character streams to byte streams. It encodes Characters into bytes using a specified charset. It extends an abstract class Writer. Other implementations of writer class include: _BufferedWriter_, _CharArrayWriter,_ _PipedWriter_ etc.

_BufferedReader_ or _BufferedWriter_ comes into place as a decorated reader implementation _(Decorator Pattern_), rather than directly reading from _InputStream_ and decoding it, it stores all the input stream into a buffer array. Hence we would be reading from main memory, which  is faster than reading from disk/STDIN. _BufferedReader_ reads a couple of characters from the Input Stream and stores them in a buffer, even though we only want to read a single character. 

Scanner on the other hand, is a more advanced utility than _BufferedReader, which also provides parsing .It can parse the user input and read an int, short, byte, float, long and double apart from String based on regex (sc.next\*\** pattern)._

_Putting it all together:_

* _BufferedReader is synchronous while Scanner is not. BufferedReader should be used if we are working with multiple threads._
* _BufferedReader has significantly larger buffer memory than Scanner.The Scanner has a little buffer (1KB char buffer) as opposed to the BufferedReader (8KB byte buffer), but it’s more than enough._
* _BufferedReader is a bit faster as compared to scanner because scanner does parsing of input data and BufferedReader simply reads sequence of characters._
