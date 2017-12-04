---
title: Java编程思想 第13章 字符串
date: 2017-11-28 21:55:09
tags: [读书笔记, Java编程思想]
---
> 可以证明，字符串操作是计算机程序设计中最常见的行为。

## 不可变String

String对象是不可变的。查看JDK文档你就会发现，String类中每一个看起来会修改String值的方法，实际上都是创建了一个全新的String对象，以包含修改后的字符串内容。而最初的String对象则丝毫未动。

## 重载“+”与StringBuilder

String对象是不可变的，你可以给一个String对象加任意多的别名。因为String对象具有只读性，所以指向它的任何引用都不可能改变它的值，因此，也就不会对其他的引用有什么影响。

不可变性会带来一定的效率问题。为String对象重载的“+”操作符就是一个例子。用于String的“+”和“+=”是Java中仅有的两个重载过的操作符，而Java不允许程序员重载任何操作符。

> 通过javap可以反编译代码为字节码，可以像看汇编语言一样查看JVM字节码。

可以看到Java通过StringBuilder来提高性能，StringBuilder是Java SE5引入的，在这之前的是StringBuffer。后者是线程安全的，因此开销也会大些。

## 无意识递归

Java中的每个类从根本上都是继承自Object，如果在toString的中调用this，就容易导致递归调用，而这种递归是不需要的。

## String上的操作

当需要改变字符串的内容时，String类的方法都会返回一个新的String对象。同时，如果内容没有发生改变，String的方法只是返回原对象的引用而已。这可以节约存储空间以及避免额外的开销。

## 格式化输出

- printf: 类似于C中的printf，通过格式修饰符来格式化输出字符串。
- System.out.format: Java SE5引入的format方法可用于PrintStream或PrintWriter对象，通过format方法模仿自C的printf。
- Formatter类: 在Java中，所有新的格式化功能都由java.util.Formatter类处理。可以将Formatter看作一个翻译器，它将格式化字符串与数据翻译成需要的结果。

## 正则表达式

正则表达式体现了Java在字符串处理方面的能力，Java的正则同其他语言没有什么区别，多使用就能熟练正则的语法。

## 扫描输入

一般解决从文件或标准输入读取数据的方法是读入一行文本，对其进行分词，然后使用Integer、Double等类的各种解析方法来解析数据。

Java SE5新增了Scanner类，它可以大大减轻扫描输入的工作负担。Scanner的构造器可以接受任何类型的输入对象，包括File对象、InputStream、String等。有了Scanner，所有的输入、分词以及翻译的操作都隐藏在不同类型的next方法中。

## StringTokenizer

在Java引入正则表达式和Scanner类之前，分割字符串的唯一方法是使用StringTokenizer来分词。不过，这种方式相对复杂，有了两种新的方式后，StringTokenizer完全可以弃用了。

## 总结

随着Java的发展，Java对字符串操作越来越完善。不过还需要注意细节上的效率问题，例如恰当地使用StringBuilder。