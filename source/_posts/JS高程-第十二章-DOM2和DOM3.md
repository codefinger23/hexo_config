---
title: JS高程 第十二章 DOM2和DOM3
date: 2017-11-02 22:44:51
tags: [读书笔记, JavaScript高级程序设计]
---

> DOM作为JS操作文档的接口，经过了很长时间的发展，提供了更加丰富的功能，除了前一章对于规范的扩展，也有DOM自身的升级，这其中值得说的就是DOM2和DOM3的升级。DOM1主要定义的是HTML和XML文档的底层结构。DOM2和DOM3级则在这个结构的基础上引入了更多的交互能力，也支持更高级的XML特性。为此DOM2和DOM3级分为许多模块，分别描述DOM某个非常具体的子集。

<!--more-->

## DOM变化

DOM2和DOM3的目的在于扩展DOM API，以满足XML的所有需求。DOM2没有引入新类型，只是在DOM1的基础上增加新方法和新属性来增强既有类型。DOM3既增强了既有类型，也引入了新类型。

### 针对命名空间的变化

名空间：namespace，有了命名空间，不同XML文档的元素就可以混合在一起，构成格式良好的文档，不必担心命名冲突，这一点其实和C++的名空间类似。命名空间使用xmlns特性来表示，XHTML的命名空间是http://www.w3.org/1999/xhtml。在任何格式良好的XHTML页面中，都应该包含在<html>元素中，如下所示：

```
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Example XHTML page</title>
    </head>
    <body>
        Hello World!
    </body>
</html>
```

上述例子中，所有元素默认都是XHTML命名空间的元素，还以通过创建前缀的方式使用命名空间：

```
<xhtml:html xmlns: xhtml="http://www.w3.org/1999/xhtml">
    <xhtml:head>
        <xhtml:title>Example XHTML page</xhtml:title>
    </xhtml:head>
    <xhtml:body>
        Hello World!
    </xhtml:body>
</xhtml:html>
```
这样就可以使用带有前缀的命名空间。同时为了适应这种命名空间的变化，其他对象需要进行适应。

- Node类型
- Document类型
- Element类型

### 其他变化

- DocumentType类型变化： 新增publicId,systemId和internalSubset
- Document类型： Document类型唯一与名空间无关的变化，添加的方法importNode，可以将其他文档的导入到当前文档中。
- Node类型： 与名空间无关的变化，isSupport，判断是否支持某一特性。
- 框架变化： 可以通过frame元素获得窗口对象，而不需要通过frames集合。

## 样式

在HTML中定义样式有3种方式：通过<link/>加载外部样式表文件；通过<style>定义嵌入式样式；通过style特性。DOM2定义了一套API来应用样式。

### 访问元素样式

通过元素style属性访问样式表信息。

- 获取样式表的属性和方法
- 计算样式信息

### 操作样式表

CSSStyleSheet类型表示的是样式表，通过操作CSSStyleSheet类型来操作样式表：

- CSS规则： CSSRule对象对应样式表中每一条规则。
- 创建规则
- 删除规则

### 元素大小

DOM中没有规定如何确定元素大小，但是却与HTML元素的样式息息相关。IE首先通过定义一些属性，来确定元素大小：

- 偏移量：

![](https://codefinger.cn/wp-content/uploads/2017/11/Screen-Shot-2017-11-02-at-23.25.46.png)

- 客户区大小：

![](https://codefinger.cn/wp-content/uploads/2017/11/Screen-Shot-2017-11-02-at-23.27.13.png)

- 滚动大小：

![](https://codefinger.cn/wp-content/uploads/2017/11/Screen-Shot-2017-11-02-at-23.28.24.png)

- 确定元素大小：

## 遍历

DOM2级遍历和范围 模块定义了两个用于辅助完成顺序遍历DOM结构的类型：NodeIterator和TreeWalker

- NodeIterator: 通过节点迭代器来遍历节点
- TreeWalker: 这NodeIterator的高级版本，提供了比NodeIterator额外的方法

## 范围

范围主要是为了让开发者更好的控制页面，通过范围的设置，开发者不需要关注节点的界限，在常规的DOM操作不能有效的修改文档时，范围就可以达到目的。IE不支持DOM的范围，但是它有自己的范围。

### DOM范围

DOM2级在Document类型中定义了createRange方法，通过这个方法创建范围。DOM中的范围实际上就是创建了一个DOM片段，就可以通过代码片段就可以操作范围。主要的使用方式有如下几种：

- DOM范围的简单选择
- DOM范围的复杂选择
- 操作DOM范围内容
- 插入DOM范围内容
- 折叠DOM范围
- 比较DOM范围
- 复制DOM范围
- 清理DOM范围

### IE8及更早版本的范围

IE9支持DOM范围，但是IE8之前的版本不支持DOM范围，自己有一种类似的概念即文本范围，主要是用方式与DOM范围类似：

- 用IE范围的简单选择
- 用IE范围的复杂选择
- 操作IE范围的内容
- 折叠IE范围
- 比较IE范围
- 复制IE范围

## 小结

本章主要内容是对于方法的介绍，主要还是多使用，只需要理解即可，主要内容是DOM2级规范定义的模块，用于增强DOM。DOM2级核心模块为DOM类型引入了XML命名空间的概念，同时也得到了XHTML的支持，但是对于HTML文档没有意义。

DOM2级样式模块主要针对操作元素的样式信息开发，特性有：

- 每个元素都有关联的style对象，可以用来确定和修改行内的样式
- 可以通过getComputedStyle获得元素的计算样式
- IE不支持getComputedStyle，但是提供了currentStyle属性
- 通过document.styleSheets集合访问样式表
- 除IE外所有浏览器都支持样式表属性，但是IE都提供了自己的属性

DOM2级遍历和范围模块提供了与DOM结构交互的不同方式，简要内容如下：

- 通过NodeIterator和TreeWalker对DOM执行深度优先遍历
- NodeIterator提供了简单的移动，TreeWalker则更加高级
- 范围是DOM结构的特定部分，然后再执行相应操作
- 使用范围选取，可以在不影响整体文档结构的情况下删除文档或复制文档
- IE8及更早的版本不支持DOM2级遍历和范围模块，它自己提供了专有属性，IE9则完全支持。
