---
title: JS高程 第21章 Ajax和Comet
date: 2017-11-11 21:34:06
tags: [读书笔记, JavaScript高级程序设计]
---
> Ajax，是对Asynchrounous JavaScript + XML的简写。这一技术能够向服务器请求额外的数据而无需卸载页面，会带来更好的用户体验。这一技术改变自从Web诞生依赖就一直沿用的“单击，等待”的交互模式。Ajax技术核心是XMLHttpRequest对象，简称XHT，这是由微软首先引入的一个特性，其他浏览器提供商后来都提供了相同的实现。虽然名字中包含XML，但Ajax通信与数据格式无关；这种技术就是无须刷新页面即可从服务器取得数据，但不一定是XML数据。异步请求这种技术在Ajax出现之前就已经存在，不过那个时候叫做远程脚本，所以如果有人这么说，那必然是从业的老司机了。

<!--more-->

## XMLHttpRequest对象

微软是第一个引入XHR对象的浏览器，由于其他浏览器中对XHR的实现与IE最早的实现是兼容的，因此就可以在所有浏览器中都以相同的方式使用xhr对象。

### XHR的用法

使用XHR对象时，要调用的第一个方法是open，它接受3个参数：要发送的请求的类型(get,post等)、请求的URL和表示是否异步发送请求的布尔值。需要注意两点：

1. URL相对于执行代码的当前域
2. 调用open这个方法并不会真正发送请求，而只是启动一个请求以备发送。

要发送特定的请求，需要调用send方法，send方法接收一个参数，即要作为请求主体发送的数据。如果不需要通过请求主体发送数据，则必须传入null，因为这个参数对某些浏览器来说是必须的。在收到响应后，响应的数据会自动填充XHR对象的属性。

- responseText：作为响应主体返回的文本。
- responseXML：如果响应的内容类型是text/xml或application/xml，这个属性中将保存包含着响应数据的XML DOM文档。
- status：响应的HTTP状态。
- statusText：HTTP状态的说明。

异步请求与同步请求不同，需要检测readyState属性，该属性表示请求/响应过程的当前活动阶段。这个属性的可取值如下：

- 0:未初始化。尚未调用open方法。
- 1:启动。已经调用open方法，但尚未调用send方法。
- 2:发送。已经调用send方法，但尚未接收到响应。
- 3:接收。已经接收到部分响应数据。
- 4:完成。已经接收到全部响应数据，而且已经可以在客户端使用。

只要readyState属性的值由一个值变成另一个值，都会触发一次readystatechange时间。可以利用这个事件来检测每次状态变化后readyState的值。

另外，在接收到响应之前还可以调用abort方法来取消异步请求，调用这个方法后，XHR对象会停止触发事件，而且也不再允许访问任何与响应有关的对象属性。在终止请求之后，还应该对XHR对象进行解引用操作。

### HTTP头部信息

每个HTTP请求和响应都会带有相应的请求信息，其中有的对开发人员游泳，有的也没什么用。XHR对象也提供了操作这两种头部(即请求头部和响应头部)信息的方法。

- Accept:浏览器能够处理的内容类型。
- Accept-Charset：浏览器能够显示的字符集。
- Accept-Encoding：浏览器能够处理的压缩编码。
- Accept-Language：浏览器当前设置的语言。
- Connection：浏览器与服务器之前连接的类型。
- Cookie：当前页面设置的任何Cookie。
- Host：发出请求的页面所在的域。
- Referer：发出请求的页面的URI。注意，HTTP规范将这个头部字段拼写错了，而为了保证与规范一致，也只能将错就错了。
- User-Agent：浏览器的用户代理字符串。

### GET请求

GET请求经常发生的一个错误，就是查询字符串的格式有问题。查询字符串中每个参数的名称和值都必须使用encodeURIComponent进行编码，然后才能放到URL的末尾；而且所有键值对都必须是由&字符分隔。

### POST请求

默认情况下，服务器对POST请求和提交Web表单的请求并不会一视同仁。因此，服务器端必须有程序来读取发送过来的原始数据，并从中解析出有用的部分。不过，可以使用XHR来模仿表单提交：首先将Content-Type头部信息设置为application/x-www-form-urlencoded，也就是表单提交的内容类型，其次是以适当的格式创建一个字符串。

## XMLHttpRequest 2级

鉴于XHR已经得到广泛的接受，成为了事实标准。W3C也着手制定相应的标准以规范其行为。XHR 1级只是把已有的XHR对象的实现斜街描述出来。而XHR 2级则进一步发展了XHR。

### FormData

现代Web应用中频繁使用的一项功能就是表单数据的序列化，XHR 2级为此定义了FormData类型。FormData为序列化表单以及创建与表单格式相同的数据提供了便利。

### 超时设定

IE8为XHR对象添加了一个timeout属性，表示请求在等待响应多少毫秒之后就终止。在给timeout设置一个数值后，如果在规定的时间内浏览器还没有接收到响应，那么就会触发timeout事件，进而会调用ontimeout事件处理程序。这项功能后来也被收入了XHR 2级规范中。

### overrideMimeType方法

Firefox最早引入overrideMimeType方法，用于充血XHR响应的MIME类型。这个方法后来也被纳入XHR 2级。因为返回响应的MIME类型决定了XHR对象如何处理它，所以提供一种方法能够重写服务器返回的MIME类型是很有用的。

## 进度事件

Progress Events规范是W3C的一个工作草案，定义了与客户端服务器通信有关的事件。这些事件最早其实只针对XHR操作，但目前也被其他API借鉴。有以下6个进度事件。

- loadstart：在接收到响应数据的第一个字节时触发。
- progress：在接收响应期间持续不断地触发。
- error：在请求发生错误触发。
- abort：在因为调用abort方法而终止连接时触发。
- load：在接收到完整的响应数据时触发。
- loadend：在通信完成或者触发error、abort或load事件后触发。

每个请求从触发loadstart事件开始，接下来一个或多个progress事件，然后触发error、abort或load事件中的一个，最后以触发loadend事件结束。

## 跨源资源共享

通过XHR实现Ajax通信的一个主要限制，来源于跨域安全策略。默认情况下，XHR对象只能访问与包含它的页面位于同一个域中的资源。这种安全策略可以预防某些恶意行为。但是，实现合理的跨域请求对开发某些浏览器应用程序也是至关重要。

CORS(Cross-Origin Resource Sharing，跨源资源共享)是W3C的一个工作草案，定义了在必须访问跨源资源时，浏览器与服务器应该如何沟通。CORS背后的基本思想，就是使用自定义的HTTP头部让浏览器与服务器进行沟通，从而决定或响应是应该成功还是应该失败。

在发送一个请求时，需要给它附加一个额外的Origin头部，其中包含请求页面的源信息，以便服务器根据增额头部信息来决定是否给予响应。如果服务器认为这个请求可以接受，就在Access-Control-Allow-Origin头部中回发相同的源信息。

如果没有这个头部，或者有这个头部但源信息不匹配，浏览器就会驳回请求。
## 其他跨域技术

在CORS出现之前，要实现跨域Ajax通信破费一些周折。开发人员想出了办法，利用DOM中能够执行跨域请求的功能，在不依赖XHR对象的情况下也能发送某种请求。

### 图像Ping

第一种跨域请求是使用img标签，因为一个网页可以从任意的网页中加载图像，不用担心是否跨域。因为可以动态地创建图像，使用它们的onload和onerror事件处理程序来确定是否接收到响应。

动态创建图像经常用于图像Ping。图像Ping是与服务器进行简单、单向的跨域通信方式。请求的数据是通过查询字符串形式发送的，而响应可以是任意内容，但通常是像素图或204响应。通过图像Ping，浏览器得不到任何具体的数据。

图像Ping最常用于跟踪用户点击页面或动态广告曝光次数，图像Ping有两个缺点：

1. 是能发送GET请求
2. 无法访问服务器的响应文本。

### JSONP

JSONP 是 JSON with padding(填充式或参数式JSON)的简写，是应用JSON的一种新方法。JSONP看起来和JSON差不多，只不过被包含在函数调用中的JSON。

JSONP由两个部分组成：回调函数和数据。回调函数是当响应到来时应当在页面中调用的函数。回调函数的名字一般是在请求中指定的。而数据就是传入回调函数中的JSON数据。

JSONP是通过动态script元素的src属性来使用的，与img属性类似，都具有跨域加载资源的能力。因为JSONP是有效的javaScript代码，所以在请求完成后，即在JSONP响应加载到页面中以后，就会立即执行。

首先，JSONP是从其他域中加载代码执行。如果其他域不安全，很可能会在响应中夹带一些恶意代码。其次，要确定JSONP请求是否失败并不容易，为此，必须设定计时器，检测指定时间内是否接收到响应。

### Comet

Comet是一种更高级的Ajax技术。Ajax是一种从页面向服务器请求数据的技术，而Comet则是一种服务器向页面推送数据的技术。Comet能够让信息近乎实时地被推送到页面上，非常适合处理体育比赛和股票报价。

有两种实现Comet的方式：长轮询和流。长轮询是传统轮询的一个翻版，传统轮询是浏览器定时向服务器发送请求，看看有没有更新数据。而长轮询把传统轮训颠倒了一下。页面发起一个服务器的请求，然后服务器一直保持连接打开，直到有数据可发送。发送完数据之后，浏览器关闭连接，随即又发起一个到服务器的新请求。

无论短轮询还是长轮询，浏览器都要在接收数据之前，先发起对服务器的连接。两者最大的区别在于服务器如何发送数据。短轮询是服务器立即发送响应，无论数据是否有效，而长轮询是等待发送响应。

第二种流行的Comet实现是HTTP流。流不同于上述两种轮询，因为它在页面的整个声明周期内只使用一个HTTP连接。具体来说，就是浏览器向服务器发送一个请求，而服务器保持连接打开，然后周期性地向浏览器发送数据。

### 服务器发送事件

SSE(Server-Sent Events，服务器发送事件)是围绕只读Comet交互推出的API或者模式。SSE API用于创建到服务器的单向连接，服务器通过这个连接可以发送任意数量的数据。服务器响应的MIME类型必须是text/event-stream，而且是浏览器中的JavaScript API能解析格式输出。SSE支持短轮询、长轮询和HTTP流，而且能在断开连接自动确定如何重新连接。有了这么简单实用的PAI，再实现Comet就容易多了。

### Web Sockets

Web Sockets的目标是在一个单独的持久连接上提供全双工、双向通信。在JavaScript中创建了Web Socket之后，会有一个HTTP请求发送到浏览器以发起连接。在取得服务器响应后，建立的连接会使用HTTP升级从HTTP协议交换为Web Socket协议。使用标准的HTTP服务器无法实现Web Sockets，只有支持这种协议的专门服务器才能正常工作。

由于Web Sockets使用了自定义的协议，所以URL模式也略有不同。未加密的连接是ws://；加密的是wss://；在使用Web Socket URL时，必须要带着这个模式，因为将来还有可能支持其他模式。

### 安全

对于未被授权系统有权访问某个资源的情况，称之为CSRF(Cross-Site Request Forgery，跨站点请求伪造)。未被授权系统会会伪装自己，让处理请求的服务器认为它是合法的。为确保通过XHR访问的URL安全，通行的做饭就是验证发送请求者是否有权访问相应的资源。一般的做法是

- 要求以SSL连接来访问可以通过XHR请求的资源
- 要求每一次请求都要附带经过相应算法计算得到的验证码。

以下措施对防范CSRF攻击不起作用。

- 邀请发送POST而不是GET请求
- 检查来源URL以确定是否可信
- 基于cookie信息进行验证

## 小结

Ajax是无需刷新页面就能够从服务器取得数据的一种方法。关于Ajax可以从以下几防霾呢来总结：

- 负责Ajax运作的核心对象时XMLHttpRequest对象。
- XHR对象是IE5最早引入，用于通过JavaScript从服务器取得XML数据。
- XHR成为了Web的一个事实标准
- 虽然实现存在差异，但XHR基本用法相对规范。可以放心使用

同源策略是对XHR的一个主要约束，可以采用被认可的跨域解决方案访问跨域资源。这个方案叫做CORS(Cross-Origin Resource Sharing, 跨源资源共享)，大部分浏览器原生支持CORS。图像Ping和JSONP是另外两种跨域通信的技术，但不如CORS稳妥。

Comet是对Ajax的进一步扩展，让服务器几乎能够实时地向客户端推送数据。实现Comet的手段主要有两个：长轮询和HTTP流。所有浏览器都支持长轮询，而只有部分浏览器原生支持HTTP流。SSE是一种实现Comet交互的浏览器API，既支持长轮询，也支持HTTP流。

Web Sockets是一种与服务器进行全双工、双向通信的信道。与其他方案不同，Web Sockets不实用HTTP协议，而使用一种自定义的协议。这种协议专门为跨素传输小数据设计。虽然要求使用不同的Web服务器，但却具有速度上的优势。