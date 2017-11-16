---
title: JS高程 第十八章 JavaScript与XML
date: 2017-11-08 22:20:25
tags: [读书笔记, JavaScript高级程序设计]
---
> XML曾一度成为存储和通过因特网传输结构化数据的标准。DOM规范的制定，不仅是为了方便在Web浏览器中使用XML，也是为了在桌面及服务器应用程序中处理XML数据。此前，由于浏览器无法解析XML数据，很多开发人员都要手动编写自己的XML解析器。而自从DOM出现后，所有浏览器都内置了对XML的原生支持，同时也提供了一系列相关的技术支持。
<!--more-->

## 浏览器对XML DOM的支持

在正式的规范诞生以前，浏览器提供商实现的XML解决方案不仅对XML的支持程度参差不齐，而且对同一特性的支持也各不相同。DOM2级是第一个提到动态床阿金XML DOM概念的规范。DOM3级进一步增强了XML DOM，新增了解析和序列化等特性。然而，当DOM3级规范的各项条款尘埃落定之后，大多数浏览器也都实现了各自不同的解决方案。

### DOM2级核心

DOM2级在domcument.implementation中引入了createDocument方法。该方法可以用来创建一个只带有根元素的空白XML文档。

### DOMParser类型

为了将XML解析为DOM文档，Firefox首先引入了DOMParser类型；后台其他浏览器也支持了这个类型。在解析XML之前，首先必须创建一个DOMParser的实例，然后再调用parseFromString方法。这个方法接收两个参数：要解析的XML字符串和内容类型。返回值是Document实例。

DOMParser只能解析格式良好的XML，因而不能把HTML解析为HTML文档。在发生解析错误时，仍然会从parseFromString中返回一个Document对象，但这个对象的文档元素时parsererror，而文档元素的内容是对解析错误的描述。

### XMLSerializer类型

在引入DOMParser的同时，同时还引入了XMLSerializer类型，提供了相反的功能：将DOM文档序列化为XML字符串。首先创建XMLSerializer的实例，然后将文档传入其serializeToString方法。但是serializeToString方法返回的字符串不适合打印，因此看起来会显得乱糟糟的。

## 浏览器对XPath的支持

XPath时设计用来在DOM文档中查找节点的一种手段，因而对XML处理也很重要。但是，DOM3级以前的标准并没有就XPath的API作出规定；XPath是在DOM3级XPath模块中首次跻身推荐标准行列的。

### DOM3级XPath

DOM3级XPath规范定义了在DOM中对XPath表达式求值的接口。在DOM3级XPaht规范定义的类型中，最重要的两个类型是XPathEvaluator和XPathResult。XPathEvaluator用于在特定的上下文中对XPath表达式求值。这个类型有下列3个方法。

- createExpression(expression, nsresolver): 将XPath表达式及相应的命名空间信息转换成一个XPAthExpression，这是查询的变异版。在多次使用同一个查询时很有用。
- createNSResolver(node): 根据node的命名空间信息创建一个新的XPathNSResolver对象。在基于使用命名空间的XML文档求值时，需要使用XPathNSResolver对象。
- evaluate(expression, context, nsresolver, type, result): 在给定的上下文中，基于给定的命名空间来对XPath表达式求值。剩下的参数指定如何返回结果。

## 浏览器对XSLT的支持

XSLT是与XML相关的一种技术，它利用XPath将文档从一种表达形式转换成另一种表现形式。与XML和XPath不同，XSLT没有正式的API，在正式的DOM规范中也没有它的位置。结果，只能依靠浏览器开发商以自己的方式来实现它。IE是第一个支持通过JavaScript处理XSLT的浏览器。

### IE中的XSLT

在IE对其他XML功能的支持一样，它对XSLT的支持也是通过ActiveX对象实现的。从IE6.0的时代起，IE就支持通过JavaScript实现完整的XSLT1.0操作。IE9中通过DOMParser创建的DOM文档不能使用XSLT。

### XSLTProcessor类型

Mozilla通过在Firefox中创建新的类型，实现了JavaScript对XSLT的支持。开发人员可以通过XSLTProcessor类型使用XSLT类型转换XML文档，其方式与在IE中国年使用XSL处理器类似。因为这个类型是率先出现的，所以其他浏览器借鉴了相同的实现，最终使XSLTProcessor成为了通过JavaScript进行XSLT转换的事实标准。

## 小结

JavaScript对XML及其相关技术有相当大的支持。然而，由于缺乏规范，共同的功能却存在一些不同的实现。DOM2级提供了创建空XML文档的API，但没有涉及解析和序列化。因此各浏览器都有自己的实现，其中最流行的就是Firefox的DOMParser类型和XMLSerializer类型。

DOM3级引入了一个针对XPath API的规范，该规范由Firefox，Safari，Chrome和Opera实现。这些API可以让JavaScript基于DOM文档运行任何XPath查询，并且们能够返回任何数据的结果。

与XML相关的最后一种技术是XSLT，没有公开发布的标准针对这种技术的功能定义相应的API。Firefox，Safari，Chrome，Opera都采用通过JavaScript处理转换创建了XSLTProcessor类型；IE则针对XSLT提供了自己的方案，一个是简单的transformNode方法，另一个是较为复杂的模板／处理器手段。