---
title: Java编程思想 第17章 容器深入研究
date: 2017-12-02 18:55:12
tags: [读书笔记, Java编程思想]
---
> 第11章介绍了Java容器类库的概念和基本功能，这些对于使用容器来说已经足够了。本章将更深入地探索这个重要的类库。
<!--more-->
## 完整的容器分类法

![](https://codefinger.cn/wp-content/uploads/2017/12/Java容器类库简化图.png)

## 填充容器

虽然容器打印的问题解决了，容器的填充仍然像java.util.Arrays一样面临同样的不足。就像Arrays一样，相应的Collections类也有一些实用的static方法，其中包括fill。与Arrays版本一阿姨那个，此fill方法也是只复制同一个对象引用来填充整个容器的，并且只对List对象有用，但是所产生的列表可以传递给构造器或addAll方法。

## Collection的功能方法

Colletion执行的所有操作都是可通过Set或List执行的所有操作。Map不是继承自Collection。

## 可选操作

执行各种不同的添加和移除的方法在Collection接口中都是可选操作。这意味着实现类并不需要为这些方法提供功能定义。

## List的功能方法

基本的List很容易使用：大多数时候只是调用add添加对象，使用get一次取出一个元素，以及调用iterator获取用于该序列的Iterator。

## Set和存储顺序

在第11章中的Set实例对可以用基本的Set执行的操作，提供了很好的介绍。但是那些示例很方便地使用了诸如Integer和String这样的Java预定义的类型，这些类型被设计为可以在容器内部使用。当创建自己的类型时，要意识到Set需要一种方式来维护存储顺序，而存储顺序如何维护，则是在Set的不同实现之间会有所变化。因此，不同的Set实现不仅仅具有不同的行为，而且它们对于可以在特定的Set中放置的元素的类型也有不同的要求。

## 队列

除了并发应用，Queue在Java SE5中仅有的两个实现是LinkedList和PriorityQueue，它们的差异在于排序行为而不是性能。

## 理解Map

映射表的基本思想是它维护的是键值对关联，因此可以使用键来查找值。标准的Java类库包含了Map的集中基本实现，包括：HashMap,TreeMap,LinkedHashMap,WeakHashMap,ConcurrentHashMap,IdentityHashMap。它们都有同样的基本接口Map，但是行为特性各不相同，这表现在效率、键值对的保存及呈现次序、对象的保存周期、映射表如何在多线程程序中工作和判定键等价的策略等方面。

## 散列与散列码

Object默认的hashCode方法获取散列码是采用对象的地址计算散列码。需要重写hashCode与equals方法才能在容器中生效。

## 选择接口的不同实现

实际上只有四种容器：Map、List、Set和Queue，如何去选择接口需要知道是采用什么样的数据结构。才能判断出那种性能最适合满足需求。

## 实用方法

Java中有大量用于容器的卓越的实用方法，它们被表示为java.util.Collections类内部的静态方法。

## 持有引用

java.lang.ref类库包含一组类，这些类为垃圾回收提供了更大的灵活性。当存在可能会耗尽内存的大对象的时候，这些类显得特别有用。有三个继承自抽象类Reference的类：SoftReferencce、WeakReference和PhantomReference。当垃圾回收器正在考察的对象之恩那个通过某个Reference对象才可获得时，上述这些不同的派生类为垃圾回收器提供了不同级别的间接性提示。

## Java 1.0/1.1 的容器

- Vecator和Enumeration
- Hashtable
- Stack
- BitSet

## 总结

可以证明，容器类库对于面向对象语言来说时最重要的类库。大多数编程工作对容器的使用比对其他类库的构件都要多。某些编程语言(如Python)甚至包含内建的基本容器构件(列表、映射表和集)。