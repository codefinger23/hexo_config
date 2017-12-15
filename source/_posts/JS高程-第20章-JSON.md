---
title: JS高程 第20章 JSON
date: 2017-11-10 22:24:50
tags: [读书笔记, JavaScript高级程序设计]
---
> 曾经一段时间，XML风靡一时，成为了互联网结构化数据传输的标准。Web服务的第一次浪潮很大程度上都是建立在XML之上，突出的特点是服务器与服务器通信。然而，业界一直不乏质疑XML的声音。不少人认为XML过于繁琐，冗长。为了解决这个问题，出现了JSON(JavaScript Object Notation, JavaScript对象表示法)，从2001年就开始了JSON的应用，它是JavaScript的一个严格的子集，利用JavaScript中的一些模式来表示结构化数据。因为可以把JSON直接传给eval()，而且不必创建DOM对象。关于JSON，最重要的是理解它是一种数据格式，不是一种编程语言。虽然具有相同的语法形式，但JSON并不从属于JavaScript。

<!--more-->

## 语法

JSON的语法可以表示下列三种类型：

- 简单值：使用与JavaScript相同的语法，可以在JSON中表示字符串、数值、布尔值和null。但JSON不支持JavaScript中的特殊值undefined。
- 对象：对象作为一种复杂的数据类型，表示的是一组无序的键值对。而每个键值对中的值可以是简单值，也可以是复杂数据类型的值。
- 数组：数组也是一种复杂数据类型，表示一组有序的值的列表，可有通过数值索引来访问其中的值。数组的值也可以是任意类型——简单值、对象或数组。

JSON不支持变量、函数或对象实例，它就是一种表示结构化数据的格式，虽然与JavaScript中表示数据的某些语法相同，但它并不局限于JavaScript的范畴。

## 解析与序列化

JSON之所以流行，拥有与JavaScript类似的语法并不是全部原因。更重要的一个原因是，可以把JSON数据结构解析为有用的JavaScript对象。与XML数据结构要解析成DOM文档而且从中提取数据极为麻烦相比，JSON可以解析为JavaScript对象的优势及其明显。

### JSON对象

早起的JSON解析器基本上就是使用JavaScript的eval函数。由于JSON是JavaScript语法的子集，因此eval函数可以解析、解释并返回JavaScript对象和数组。ECMAScript5对解析JSON的行为进行规范，定义了全局对象JSON。对于较早版本的浏览器，可以使用一个shim:https://github.com/douglascrockfor/JJSON-js。在旧版本的浏览器总，使用eval对JSON数据结构求值存在风险，因为可能会执行一些恶意代码。对于不能支持原生支持JSON解析的浏览器，使用这个shim是最佳选择。

### 序列化选项

实际上，JSON.stringify()除了要序列化的JavaScript对象外，还可以接受另外两个参数，这两个参数用于指定以不同的方式序列化JavaScript对象。第一个参数是个过滤器，可以是一个数组，也可以是一个函数；第二个是一个选项，表示是否在JSON字符串中保留缩进。单独或组合使用这两个参数，可以更全面深入地控制JSON的序列化。

### 解析选项

JSON.parse方法也可以接收另一个参数，该参数是一个函数，将在每个键值对调用。为了区别JSON.stringify接收的替换函数，这个函数被成为还原函数，但实际上这两个函数的签名是相同的——它们都接收两个参数，一个键和一个值，而且都需要返回一个值。

## 小结

JSON是一个轻量级的数据格式，可以简化比噢哈斯复杂数据结构的工作量。JSON使用JavaScript语法的子集表示对象、数组、字符串、数值、布尔值和null。即使XML也能表示同样复杂的数据结果，但JSON没有那么繁琐，而且在JavaScript中使用更便利。

ECMAScript5定义了一个原生的JSON对象，可以用来将对象序列化为JSON字符串或者将JSON数据解析为JavaScript对象。JSON.stringigy和JSON.parse方法分别用来实现上述两项功能。这两个方法都有一些选项，通过他们可以改变过滤的方式，或者改变序列化的过程。