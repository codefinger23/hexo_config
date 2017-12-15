---
title: JS高程 第二章 在HTML中使用JS
date: 2017-10-19 22:08:43
tags: [读书笔记, JavaScript高级程序设计]
---
> 在HTML中使用JavaScript是一件很简单的事情，但是，经常写前端的小伙伴们，你们真的没有想过为什么要这么写么？

<!--more-->

## &lt;script&gt; 标签

向HTML页面插入JavaScript元素的主要方法就是使用&lt;script&gt;标签，这个元素也是Netscape公司创造，后来被正式加入到HTML规范，注意这是HTML规范，而不是js的。

&lt;script&gt;标签有很多属性，主要有以下几种，虽然不常用，但是在script标签出现时应该知道:

- async: 可选。只对外部加载脚本文件有效，表示立即下载该脚本但是不应妨碍页面的其他操作。
- src: 可选。表示外部脚本文件的地址。
- charset: 可选。指定src属性的脚本文件编码。
- language: 已废弃。这个属性的存在是由于曾经多种存在的javascript语言，需要进行区分加载。比如JavaScript、VBScript。
- type: 可选。这个算是language的替代，让浏览器能够识别出是，需要看下MIME对javascript的定义，一般是text/javascript，目前来说记住这个就可以的。
- defer: 可选。只对外部文件有用，表示延迟加载，直到整个页面加载完成后再加载文件。

使用&lt;script&gt;元素有两种方式，一种是页面嵌入，一种是外部文件。

javascript解释器是从上到下依次解释，需要注意的是如果想要使用函数，就需要先定义。

> * 当使用嵌入&lt;script&gt;代码不能在代码中包含&lt;/script&gt; 因为这是&lt;script&gt;标签的结束
> * 外部引入文件的后缀通常是.js，但这不是必须的，也就是说可以通过jsp, php来生成动态的js文件，但是当后缀不是.js时，需要返回正确的MIME，具体可以参考HTTP权威指南对于MIME的定义。
> * 嵌入&lt;script&gt;代码会从上到下依次解释，因为javascript通常是表单验证等无关页面渲染的附加功能，所以如果按照通常情况写在<header>中，会导致页面加载减慢，所以目前通常会放到页面尾。但是可以通过defer或async控制加载。
> * 外部引入文件可以通过src属性引入，也可以引入外域文件，这种操作需要谨慎。

## 嵌入代码与外部文件

在html中嵌入javascript代码，虽然没有问题，但一般认为最好的做法还是尽可能使用外部文件来包含javascript代码，不过并不存在必须使用外部文件的硬性规定，但支持使用外部文件的人会强调以下优点：

- 可维护性： 遍及不同html页面的java会不会造成维护问题，但把所有javascript文件都放在一个文件夹中维护起来就轻松多了。
- 可缓存：浏览器能够根据具体的设置缓存连接所有外部加载的javascript文件，也就是说如果有两个页面都使用同一个文件，那么这个文件只需下载一次，最终，就可以加快页面加载速度。
- 适应未来，通过外部加载javascript文件可以适应所有的不同需求，而不需要通过特殊设置来进行语法识别。

## 文档模式

文档模式一般是影响CSS页面渲染效果，但是有些情况下也会影响javascript的执行。主要有两种文档模式：混杂模式和标准模式。使用标准模式声明，则必须对应标准的javascript代码，一些不符合声明标准的特性则不可以使用，比如java8和java7的区别。如果文档开始没有进行模式声明，则默认采用混杂模式，这部分内容比较难以呈现，采用截图来作为参考。
![](https://codefinger.cn/wp-content/uploads/2017/10/Screen-Shot-2017-10-30-at-14.28.57.png)
## &lt;noscript&gt; 标签

&lt;noscript&gt; 主要是为了在不能运行javascript代码时进行的页面降级，&lt;noscript&gt;中的元素只会在两种情况下呈现：

- 浏览器不支持javascript
- 浏览器禁用了javascript

在启用了javascript的浏览器中,&lt;noscript&gt;渲染的所有元素都不会被渲染。

## 小结

将javascript代码嵌入到html文档中需要使用&lt;script&gt;标签。也可以通过外部文件调用javascript代码。因为javascript代码会被顺序加载，所以需要提前定义要使用的函数。为了不影响页面加载速度。javascript通常放在页面最下方进行加载。noscript中的元素只会在浏览器不能运行javascript的情况下被展示。