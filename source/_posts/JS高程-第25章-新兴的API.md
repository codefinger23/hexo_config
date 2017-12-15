---
title: JS高程 第25章 新兴的API
date: 2017-11-15 22:29:40
tags: [读书笔记, JavaScript高级程序设计]
---
> 随着HTML5的出现，面向未来Web应用的JavaScript API也得到了极大的发展。这些API没有包含在HTML5规范中，而是各自有各自的规范。但是，他们都属于“HTML5相关的API”。

<!--more-->

## requestAnimationFrame

很长时间以来，计时器和循环间隔一直都是JavaScript动画的最核心技术。虽然CSS变换及动画为Web开发人员提供了实现动画的简单手段，但JavaScript动画开发领域的状况这些年来并没有大的变化。

### 早期动画循环

在JavaScript中创建动画的典型方式，就是使用setInterval方法来控制所有动画。

### 循环间隔问题

知道什么时候绘制下一帧是保证动画平滑的关键。然而，直至最近，开发人员都没有办法确保浏览器按时绘制下一帧。随着canvas元素越来越流行，新的基于浏览器的游戏也崭露头脚，面对不十分精确的setInterval和setTimeout。

## Page Visibility API

不知道用户是不是正在与页面交互，这是困扰广大Web开发人员的一个主要问题。如果页面最小化了或者隐藏在了其他标签页后面，那么有些功能是可以停下来的，比如轮询服务器或者某些动画效果。而Page Visibvility API就是为了让开发人员知道页面是否对用户可见而推出的。

这个API本身非常简单，由以下三部分组成：

- document.hidden: 表示页面是否隐藏的布尔值。页面隐藏包括页面在后台标签页中或者浏览器最小化。
- document.visibilityState: 表示4个可能的状态的值
>* 页面在后台标签页中或浏览器最小化
>* 页面在前台标签页中
>* 实际的页面已经隐藏，但用户可以看到页面的预览
>* 页面在屏幕外执行预渲染处理
- visibilitychange时间：当文档从可见变为不可见或从不可见变为可见时，触发该事件。

## Geolocation API

地理定位是最令人兴奋，而且得到了广泛支持的一个新API。通过这套API，JavaScript代码能够访问到用户的当前位置信息。当然，访问之前必须得到用户的明确许可，即同意在页面中共享其位置信息。如果页面尝试访问地理定位信息，浏览器就会显示一个对话框，请求用户许可共享其位置信息。

## File API

不能直接访问用户计算机中的文件，一直都是Web应用开发中的一大障碍。2000年以前，处理文件的唯一方式就是在表单中加入input type="file" 字段，仅此而已。File API 的宗旨是为Web开发人员提供一种安全的方式，以便在客户端访问用户计算机中的文件，并更好地对这些文件执行操作。

File API在表单中的文件输入字段的基础上，又添加了一些直接访问文件信息的接口。H5在DOM中为文件输入元素添加了一个files集合。在通过文件输入字段选择了一或多个文件时，files集合中将包含一组File对象对应着一个文件。每个File对象都有下列只读属性。

- name: 本地文件系统中的文件名。
- size：文件的字节大小。
- type：字符串，文件的MIME类型
- lastModifiedDate：字符串，文件上一次被修改的事件。

### FileReader类型

FileReader类型实现的额时一种异步文件读取机制。可以把FileReader想象成XMLHttpRequest，区别只是它读取的是文件系统，而不是远程服务器。为了读取文件中的数据，FileReader提供了如下几个方法：

- readAsText(file, encoding): 以纯文本形式读取文件，将读取文本保存在result属性中。第二个参数用于指定编码类型，是可选的。
- readAsDataURL(file): 读取文件并将文件以数据URI的形式保存在result属性中
- readAsBinaryString(file): 读取文件并将一个字符串保存在result属性中，字符串中的每个字符表示一字节。
- readAsArrayBuffer(file): 读取文件并将一个包含文件内容的ArrayBuffer保存在result属性中。

### 读取部分内容

有时候，我们只想读取文件的一部分而不是全部内容。为此，File对象还支持一个slice方法。这个方法接收两个参数：起始字节及要读取的字节数。这个方法返回一个Blob的实例，Blob是File类型的父类型。

### 对象URL

对象URL也被称为blob URL，指的是引用保存在File或Blob中数据的URL。使用对象URL的好处是可以不必把文件内容读取到JavaScript中而直接使用文件内容。为此，只要在需要文件内容的地方提供对象URL即可。

## Web 计时

页面性能一直是Web开发人员最关注的领域。但直至最近，度量页面性能指标的唯一方式，就是提高代码复杂度和巧妙地使用JavaScript的Date对象。Web Timing API改变了这个局面，让开发人员通过JavaScript就能使用浏览器内部的度量结果，通过直接读取这些信息可以做任何想做的分析。

## Web Workers

随着Web应用复杂性的与日俱增，越来越复杂的计算在所难免。长时间运行的JavaScript进程会导致浏览器冻结用户界面，让人感觉屏幕冻结了。Web Workers规范通过让JavaScript在后台运行解决了这个问题。浏览器实现Web Workers规范的方式有很多种，可以使用线程、后台进程或者运行在其他处理器核心上的进程。具体的实现细节其实没有那么重要，重要的是开发人员现在可以放心地运行JavaScript，而不必担心会影响用户体验了。

## 小结

与HTML5同时兴起的是另外一批JavaScript API。从技术规范角度讲，这批API不属于HTML5，但从整体上可以称它们为HTML5 JavaScript API。这些API的标准有不少虽然还在制定当中，但已经得到了浏览器广泛支持。