---
title: JS高程 第一章 JS简史
date: 2017-10-19 22:08:21
tags: 读书笔记
---
## 简史
javascript的产生的原因是为了解决日益增长的页面交互与缓慢网速的矛盾，在javascript产生的年代，即1995年，网速相当缓慢，那个时候还是通过电话线进行互联网链接，通过调制解调器也就是“猫”来上网，网速是当今社会无法想象的， 此时如果一个简单的表单验证也需要与服务器交互，无疑是自寻死路。

为了增加用户的浏览体验，Netscape公司最早开始了在浏览器中嵌入执行脚本来进行表单验证，在其公司开发的浏览器中嵌入了最早的脚本处理器。名为LiveScript的脚本语言，后来未来蹭java的热度，更名为JavaScript。

Netscape公司的浏览器策略大获全胜，在当时一度成为市场领袖，而当时很流弊的微软公司，为了撕下一口浏览器市场，在windows自带的IE浏览器中也加入了自己的脚本语言，名为JScript，是为了避免Netscape公司的授权，由于其操作系统自带的天然优势，当时的微软简直是巨无霸的，虽然当时还没有流量一说，但是，无疑收获了巨大成功，也为Netscape的落幕埋下伏笔。

由于当时没有标准规定JavaScript的语法和特性，所以市场上就存在了两种比较流行的JavaScript脚本，就是Netscape和微软的两种，当然还有其他版本的，和现在各类市场百花齐放大相径庭。

1997年，以JavaScript 1.1为蓝本的建议被提交给了欧洲计算机制造商协会（ECMA，European Computer Manufacturers Association）。该协会指定39号技术委员会（TC39，Technical Committee #39）负责“标准化一种通用、跨平台、供应商中立的脚本语言的语法和语义”（http://www.ecma-international.org/memento/TC39.htm）。TC39由来自Netscape、Sun、微软、Borland及其他关注脚本语言发展的公司的程序员组成，他们经过数月的努力完成了ECMA-262——定义一种名为ECMAScript（发音为“ek-ma-script”）的新脚本语言的标准。

第二年，ISO/IEC（International Organization for Standardization and International Electrotechnical Commission，国标标准化组织和国际电工委员会）也采用了ECMAScript作为标准（即ISO/IEC-16262）。自此以后，浏览器开发商就开始致力于将ECMAScript作为各自JavaScript实现的基础，也在不同程度上取得了成功。

ECMAScipt 即常说的ES语法规范，讲的就是JavaScript应该遵循既实现的各种功能。

## 实现

![alt](https://codefinger.cn:444/static/upload/20171012/513DXLqIfALKp4XRevwMEfl4.png)

JavaScript由上图三个不同的部分组成
- 核心（ECMAScript）
- 文档对象模型（DOM）
- 浏览器对象模型（BOM）

### ECMAScipt

既然ECMA-262标准没有参照Web浏览器，那它都规定了些什么内容呢？大致说来，它规定了这门语言的下列组成部分：

- 语法

- 类型

- 语句

- 关键字

- 保留字

- 操作符

- 对象

ECMAScript就是对实现该标准规定的各个方面内容的语言的描述。JavaScript实现了ECMAScript，Adobe ActionScript同样也实现了ECMAScript。

### 文档对象模型（DOM）

DOM= Document Object Model，文档对象模型，DOM可以以一种独立于平台和语言的方式访问和修改一个文档的内容和结构。换句话说，这是表示和处理一个HTML或XML文档的常用方法。有一点很重要，DOM的设计是以对象管理组织（OMG）的规约为基础的，因此可以用于任何编程语言。最初人们把它认为是一种让JavaScript在浏览器间可移植的方法，不过DOM的应用已经远远超出这个范围。Dom技术使得用户页面可以动态地变化，如可以动态地显示或隐藏一个元素，改变它们的属性，增加一个元素等，Dom技术使得页面的交互性大大地增强。

### 浏览器对象模型（BOM）

Internet Explorer 3和Netscape Navigator 3有一个共同的特色，那就是支持可以访问和操作浏览器窗口的浏览器对象模型（BOM，Browser Object Model）。开发人员使用BOM可以控制浏览器显示的页面以外的部分。而BOM真正与众不同的地方（也是经常会导致问题的地方），还是它作为JavaScript实现的一部分但却没有相关的标准。这个问题在HTML5中得到了解决，HTML5致力于把很多BOM功能写入正式规范。HTML5发布后，很多关于BOM的困惑烟消云散。

从根本上讲，BOM只处理浏览器窗口和框架；但人们习惯上也把所有针对浏览器的JavaScript扩展算作BOM的一部分。下面就是一些这样的扩展：

- 弹出新浏览器窗口的功能；

- 移动、缩放和关闭浏览器窗口的功能；

- 提供浏览器详细信息的navigator对象；

- 提供浏览器所加载页面的详细信息的location对象；

- 提供用户显示器分辨率详细信息的screen对象；

- 对cookies的支持；

- 像XMLHttpRequest和IE的ActiveXObject这样的自定义对象。

由于没有BOM标准可以遵循，因此每个浏览器都有自己的实现。虽然也存在一些事实标准，例如要有window对象和navigator对象等，但每个浏览器都会为这两个对象乃至其他对象定义自己的属性和方法。现在有了HTML5，BOM实现的细节有望朝着兼容性越来越高的方向发展。第8章将深入讨论BOM。

## 小结

JavaScript是一种专为与网页交互而设计的脚本语言，由下列三个不同的部分组成：

- ECMAScript，由ECMA-262定义，提供核心语言功能；

- 文档对象模型（DOM），提供访问和操作网页内容的方法和接口；

- 浏览器对象模型（BOM），提供与浏览器交互的方法和接口。

JavaScript的这三个组成部分，在当前五个主要浏览器（IE、Firefox、Chrome、Safari和Opera）中都得到了不同程度的支持。其中，所有浏览器对ECMAScript第3版的支持大体上都还不错，而对ECMAScript 5的支持程度越来越高，但对DOM的支持则彼此相差比较多。对已经正式纳入HTML5标准的BOM来说，尽管各浏览器都实现了某些众所周知的共同特性，但其他特性还是会因浏览器而异。
