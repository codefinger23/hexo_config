---
title: JS高程 第十一章 DOM扩展
date: 2017-11-01 21:52:13
tags: [读书笔记, JavaScript高级程序设计]
---
> 上一章讲述了文档对象模型(DOM)的基础内容，虽然已经足够强大，但是在使用过程中仍然显得不方便，因此各浏览器厂商为了凸显自己产品的强大，添加了对于DOM API的扩展，W3C已经着手将一些专有扩展标准化，以便降低各个浏览器之间的不同。这其中两个主要的扩展是Selectors API和HTML5。
<!--more-->

## 选择符API(Selectors API)

众多JavaScript库中最常用的一项功能就是根据CSS选择符选择与某个模式匹配的DOM元素，实际上JQuery的核心就是通过CSS选择符查询DOM文档以取得某个元素的引用，从而抛开getElementById和getElementByTagName的使用，Selectors API就是W3C发起制订的一个标准，通过原生的浏览器支持，极大的提升性能，最主要的就是两个方法querySelector和querySelectorAll。

- querySelector: 该方法接受一个CSS选择符，返回与该模式匹配的第一个元素，如果没有找到，返回null。
- querySelectorAll: 该方法同样接受一个CSS选择符，但是会返回与该模式匹配的所有元素，以NodeList的形式返回，这里的NodeList非动态查询，而是相当于一个快照，以此提升性能。
- matchesSelector: 该方法和上面两个方法相同，接受一个CSS选择符，返回值是调用元素是否匹配该模式。

## 元素遍历

由于元素之间的空白字符的处理行为不同，有的会将空白字符当成文本节点，有的不会，因此有一种DOM扩展就是专门用于元素遍历，即Element Traversal规范，该规范定义的属性只返回元素节点而没有文本节点，主要属性如下：

- childElementCount: 返回子元素个数，不包括文本节点
- firstChildElement: 第一个元素节点
- lastChildElement: 最后一个元素节点
- previousChildSibling: 前一个同辈元素节点
- nextChildSibling: 后一个同辈元素节点

## HTML5

H5实际上就是定义了很多新的API的HTML，通过扩充JavaScript的行为，能够支持更多的行为，让开发者更方便的开发出优秀的网络程序。

### 与类相关的扩展

HTML文档的不断发展，对于标签的class属性有了更多的使用，同时也通过class属性，将标签与对应的css样式对应起来，所以在H5的规范中，增强了类相关的行为。

- getElementByClassName: 通过class属性获得元素。
- classList: 获得元素的class列表。能够在只修改部分class的情况下不需要重写整个className字段。

### 焦点管理

H5也添加了辅助管理DOM焦点的功能，帮助开发者快速获得用户焦点，主要使用在页面加载和输入行为的识别。元素获得焦点的主要方式是通过focus方法，能够让指定的元素获得焦点。

通过document.activeElement可以获得焦点元素。还可以通过document.hasFocus方法确认文档是否获得焦点。

### HTMLDocument 变化

H5同样扩展了HTMLDocument，增加了新的功能。

- readyState属性： 该属性为loading表示正在加载文档，为complete表示文档以加载完成。
- 兼容模式： 通过添加document.compatMode确认浏览器是以标准模式渲染还是混杂模式。标准模式下值为"CSS1Compat"，混杂模式下为BackCompat。
- head属性： 作为document.body引用文档的补充，通过document.head快速获取对head的引用。

### 字符集属性

通过document.charset属性直接表示文档所用的字符集，一般是通过<meta>元素进行设置。为了避免默认字符编码导致乱码的选择。

### 自定义数据属性

H5支持为元素添加非标准的属性，但是需要添加data-前缀，所有的这类自定义属性都会放置在元素的dataset属性中，dataset是DOMStringMap的一个实例，存储键值对，分别是属性名和属性值，需要注意的是，通过dataset获取的属性值将会自动去除data-前缀。

### 插入标记

DOM自身的接口虽然可以动态的添加各类节点，但是当有大量的html标签需要添加时，使用DOM接口进行添加是非常低效和代码冗余的，因此H5引入了批量添加替换标记的接口

- innerHTML: 读取innerHTML会获取元素的所有子元素，写模式下会将输入的内容字符串转化成html节点挂载在当前元素下。
- outerHTML: 和innerHTML类似，也是获取元素内容，区别在于操作会包括元素自身进行读取和替换。
- insertAdjacentHTML: 在指定位置插入字符串转化的html元素。位置标记有beforebegin, afterbegin, beforeend, afterend。
- 内存与性能： 需要注意的是，采用替换标记的作为，并不会释放与节点绑定的JavaScript事件的引用，在多次调用替换后会导致内存泄漏，因此在使用替换时，最好手动解除这些引用。

### scrollIntoView 方法

设置页面滚动的行为，是对DOM的一种增强，因为DOM并没有对于页面滚动相关的支持。

## 专有扩展

开篇就已经提到，各个浏览器厂商为了让自己的浏览器更加强大，因此为他们的浏览器添加了很多扩展，其中有很多被收纳为规范，但是扔有大量的没有被收入规范中的转悠扩展，这里只做介绍，并不推荐使用。

### 文档模式

文档模式决定了浏览器能够支持哪些方法和特性，是IE支持的属性，同时也有不同的文档模式支持。

### children 属性

因为不同浏览器对于元素下的空白字符的对待方式不同，有的是文本节点，有的忽略，因此children就是提取其中的元素节点。

### contains 方法

通过该方法能够知道某一个节点是不是指定节点的字节点。只能确定是不是后代的关系，DOM Level 3 支持另外一个更佳强大的方法: compareDocumentPosition，该方法通过返回掩码的方式确定两个节点的位置关系，具体如图：

![](https://codefinger.cn/wp-content/uploads/2017/11/Screen-Shot-2017-11-01-at-23.07.10.png)

### 插入文本

除了H5收录的innerHTML和outerHTML外，还有另外的几个方法可以对节点内容进行直接操作：

- innerText: 和innerHTML类似，不同点在于，读模式下返回其中所有的文本节点，写模式下将所有子元素替换为指定的文本。同时写入的文本会进行HTML转义，即特殊字符的处理。
- outerText: 和innerText不同之处在于替换时包括外部元素会都会被替换，而不单单是子元素。

### 滚动

H5仅仅将scrollIntoView收纳，这里还有其他和滚动事件相关的方法：

- scrollIntoViewNeeded(alignCenter): 只在当前元素不可见的情况下进行滚动，当alignCenter设置为true时，将会把文本显示在页面中部。
- scrollByLines: 指定元素滚动的行高。
- scrollByPage: 滚动元素到指定的页面高度。

## 小结

虽然DOM制订了与XML及HTML文档交互的核心API，但仍有几个规范对标准的DOM进行了扩展。这些扩展本来是浏览器专有的，后来成为了标准。本章主要介绍了以下三个规范：

- Selectors API，定义了两个方法，让开发人员能够基于CSS选择符获取元素，这两个方法是querySelector和querySelectorAll。
- Element Traversal， 为DOM元素制订了额外的属性，让开发者能够方便的从一个元素跳到另外的元素，之所以会有这个扩展，是因为不同浏览器处理空白字符的方式不同。
- HTML5，为标准的DOM定义了很多扩展。其中包括innerHTML属性这样的事实标准上提供的标准定义，以及为管理焦点，设置字符集，滚动页面而提供的API。

虽然目前DOM扩展的数量还不多，但是随着Web技术的发展，通过浏览器厂商不断的试验专有扩展，最终这些这些事实标准，获得认可之后都会被收录到标准规范中，成为真正意义上的标准。