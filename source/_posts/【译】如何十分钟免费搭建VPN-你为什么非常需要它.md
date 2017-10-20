---
title: 【译】如何十分钟免费搭建VPN(你为什么非常需要它)
date: 2017-10-19 19:42:53
tags: 翻译
---

> 原文：http://www.zcfy.cc/article/4254

* * *

# 如何十分钟免费搭建VPN(你为什么非常需要它)
> 导读：本文前半部分讲述了越来越危机的网络环境，后半部分从实际技术角度出发讲述了如何使用Opera浏览器在保护隐私的情况下访问网络，基于HTTPS与VPN的，同时也给出了一些保护隐私的高级建议。
> 很多人说，在当今时代，我们已经没有隐私了，但是，要记住，我们失去的只是过去，更重要的是将来。

![](http://p0.qhimg.com/t018e3ca662a89f9cef.jpg)

“摄影师与花” by Banksy. Stencil 2010年
> “A computer lets you make more mistakes faster than any other invention with the possible exceptions of handguns and Tequila.” — Mitch Ratcliffe
> “除了手枪与龙舌兰酒，计算机可能是让你更容易犯错的发明。” - 米奇·拉特克利夫
<!--more-->
你在互联网上所犯的错误很快将不仅仅被你的网络服务供应商(ISP)所知 - 也将会被任何想要知道这些错误的公司或者外国政府所知

这样的结果得感谢国会的决定。在不经过你的允许下，网络供应商们可以贩卖你整个网络浏览记录给任何人。有限的保护你的隐私不被他人所知的法律将会被废除，并且不会再被启用(国会将采取行动)

网络供应商们可以贩卖他们[想要贩卖的任何信息](https://www.washingtonpost.com/news/the-switch/wp/2017/03/28/republicans-are-poised-to-roll-back-landmark-fcc-privacy-rules-heres-what-you-need-to-know/)
包括你的在线活动，移动应用使用情况, 经济信息，医疗信息，你孩子的信息，你的社保账号-甚至包括你的电子邮箱

他们甚至可以贩卖你的地理位置。没错，网络供应商们可以可以把你每一分钟的确切位置贩卖给第三方(译者注：我们都知道这太可怕了)


你可能会想：谁会从废除这些保护中获得好处？除了[网络供应商四巨头](https://medium.freecodecamp.com/inside-the-invisible-war-for-the-open-internet-dd31a29a3f08)这些垄断了美国每一寸土地的互联网建设者？

答案是没有人。没有人会以任何方式获利。我们的隐私-我们国家的安全-逐渐被排挤，这个过程中只有几个大公司可以赚一丢丢的money。

换句话说，这些政治家-几十年来从网络供应商[收到了数百万美元的竞选捐款的人](http://www.theverge.com/2017/3/29/15100620/congress-fcc-isp-web-browsing-privacy-fire-sale)-把我们出卖了。

### 这些是怎么发生的？

1996年通过的国会审查法(CRA)，赋予了国会推翻政府条例的权利。

在2017年之前，国会只成功使用过一次国会审查法(CRA)。但自从1月份新政府换任以来，已经成功地使用了3次，例如撤销恶劣的环境法规

参议员杰夫·弗莱克(Jeff Flake)是亚利桑那州的一名共和党人，率先推翻了FCC( Federal Communications Commission, 美国联邦通讯委员会)的隐私规则。他已经是[美国最不受欢迎的参议员](https://www.theatlantic.com/politics/archive/2013/04/jeff-flake-most-unpopular-senator-america/315763/) 。现在他可能成为美国历史上最不受欢迎的参议员。

![](http://p7.qhimg.com/t019694b4fba8cd5e82.jpg)

图为弗莱克参议员

不仅仅是指责弗莱克，我们应该记住，每一位投票赞成推翻这些隐私规则的参议员都是共和党人。每一位民主党与独立参议院都反对国会审查法的决议。在两位共和党人弃权下，最终的投票结果是50-48。

你可能会以为参议院会认真讨论这样一个历史性决定所带来的后果。但实际上，[他们只讨论了10分钟](https://www.congress.gov/congressional-record/2017/03/23/senate-section/article/S1942-4)。

> “Relying on the government to protect your privacy is like asking a peeping tom to install your window blinds.” — John Perry Barlow
> “依靠政府保护你的隐私就像让偷窥者安装你的百叶窗” — 约翰·佩里·巴洛

![](http://p0.qhimg.com/t018085fd67494fd2ee.jpg)

VPN公司[私有网络接入](https://www.privateinternetaccess.com/) 在星期日的“纽约时报”上支付了60万美元来运行上面这张广告 - 即使这些规则被废除，他们也会赚很多钱。这就是国会审查法糟糕的地方 - 即使VPN公司也在反对它。

[国会审查法案](https://www.congress.gov/bill/115th-congress/senate-joint-resolution/34/text CRA)在众议院也通过了，这次有231名共和党人投票取缔隐私保护，189名民主党人投票反对它的通过。（仍然没有一个非共和党人投票取消这些隐私保护。）

剩下的就是共和党总统签署这项决议，他也说他打算这样做。

### 所以网络供应商们可以合法的使用我们的数据搞些什么幺蛾子？

根据[电子前沿基金会](https://www.eff.org/deeplinks/2017/03/five-creepy-things-your-isp-could-do-if-congress-repeals-fccs-privacy-protections)，至少有5种行为被FCC法案视为非法。但是多亏了参议院，网络供应商们现在可以继续为所欲为了，可能要过几年我们才能采取任何措施来阻止他们。

1.  把你的浏览历史卖给任何想买它的公司或政府

2.  劫持你的搜索行为分享给第三方

3.  通过在你访问的网站上注入他们自己的恶意软件来监控你的流量

4.  通过向cookie注入不可检测的代码到，追踪到你所有的非加密流量

5.  通过在手机预安装软件来监控所有的流量 - 甚至HTTPS流量 - 在加密之前。AT&T、Sprint和T-Mobile已经在一些Android手机上实现了这一目标。

### 那么我们现在怎么能保护我们的隐私呢

根据[Pew研究中心的研究](http://www.pewresearch.org/fact-tank/2016/09/21/the-state-of-privacy-in-america/)，91%的成年人非常同意“消费者已经失去了如何收集和使用个人信息的控制权。”

但我们不应该绝望。但正如英国首相警告我们“抱最好的希望，做最坏的打算”一样，他还说：
> “Despair is the conclusion of fools.” — Benjamin Disraeli in 1883
> “绝望只是傻瓜的结论” - 本杰明·迪斯雷利. 1883

我们不是傻瓜。我们将采取必要的行动，确保我们家庭的隐私不受肆无忌惮的垄断行为及其政治傀儡的侵犯。

我们要用最有效的工具，确保网上交流这样做：加密和VPN。

### 第一步: 随时随地启用HTTPS

正如上文所说，如果他们能在你的手机操作系统上安装间谍软件，网络供应商们也能在HTTPS环境下搞些毛呢。但是你能不买那些型号的手机，这时HTTPS就会给你相当安全的防御。

HTTPS通过使用安全TLS协议来加密目的站点和设备之间的通信。

问题在于，截止到2017年，只有约10%的网站已经启用HTTPS，仍然有很多网站没有开启HTTPS以保护他们与客户端的通信(即便可以通过简单免费的使用[LetsEncrypt](https://letsencrypt.org/)的情况下)

这就是EFF(Electronic Frontier Foundation,电子前哨基金会)的HTTPS Everywhere扩展功能的用武之地。它可以让这些站点默认使用HTTPS，并能在你访问这些网站时弹出非HTTPS连接的提醒。它是免费的，你可以[点此安装](https://www.eff.org/https-everywhere)。

我们可以肯定的一件事 - 这得感谢[维基解密中央情报局的黑客武器库](https://medium.freecodecamp.com/the-cia-just-lost-control-of-its-hacking-arsenal-heres-what-you-need-to-know-ea69fc1ce38c)  - 那就是只要你使用安全的加密形式[加密仍然工作](http://bigstory.ap.org/article/cf84bf54c2954de8baaa5fb6931a84d0/what-cia-wikileaks-dump-tells-us-encryption-works)，- 据我们最近所知，HTTPS的TLS加密目前还没有被破解  - 所以你的数据仍被保密。

> “The average busy professional in this country wakes up in the morning, goes to work, comes home, takes care of personal and family obligations, and then goes to sleep, unaware that he or she likely committed several federal crimes that day.” — Harvey Silverglate
> “这个国家忙碌的普通人在早上醒来，去上班，回家，履行照顾个人和家庭的以后，然后去睡觉，不知道这一天他或她可能犯了几次联邦罪行。”- 哈维·希尔维格雷特

顺便说一句，如果你还不知道，我强烈建议你看一下我的这篇文章[如果在不到一小时时间内加密你一整天的生活](https://medium.freecodecamp.com/tor-signal-and-beyond-a-law-abiding-citizens-guide-to-privacy-1a593f2104c3#.rouhl2kbf)。

但即使启用HTTPS，网络供应商们仍然能够知道知道 -多亏了他们在你连接网站过程中的作用-你真正连接的网站，即时他们不知道你在做什么。

只要知道你要去哪里-你的网络活动的“元数据”-给网络供应商们可以出售的大量信息。

例如，小明浏览Cars.com可能是要买辆新车，小红浏览BabyCenter.com可能是已经怀孕.

那就是使用VPN的地方。

### VPN是如何保护你的

VPN意思是虚拟私有网络

*  **虚拟** 因为您没有与目标建立新的物理连接-你的数据通过现有通道传输到目的主机

*  **私有** 因为它在你发送数据前加密，然后在目的主机解密。

人们通常使用VPN作为一种访问被国家封锁网站或电影的科学方法（例如，中国的防火长城）。而且VPN对于隐私保护也很有帮助。

不同的VPN选择，有不同程度的方便与安全。

专家估计[90%的VPN是非常安全的](https://www.theregister.co.uk/2016/02/26/ssl_vpns_survey/)并随时间改变。所以即使你使用我推荐的工具，我建议你还是花点时间[做功课](https://thatoneprivacysite.net/simple-vpn-comparison-chart/)为好。

### 基于浏览器的VPN

大部分VPN服务是付费的。但我推荐的第一种VPN选择是很方便且完全免费的。

Opera是一款带有一些优秀隐私特性的浏览器，比如免费嵌入的VPN和免费的广告拦截器（你懂的，广告也可以监视你）

如果你只想要一个安全的方式浏览网页，领ISP不能很容易地窥探你并出售你的数据，Opera是一个很好的开始。让我们快速安装并配置它。这需要不到5分钟。

在你开始之前，请注意，只在匿名的Opera浏览器中做你的事情。此外，我有责任指出，尽管Opera的母公司在欧洲，它最近被中国的科技公司[收购](https://www.engadget.com/2016/07/18/opera-browser-sold-to-a-chinese-consortium-for-600-million/)，在中国政府的干涉下，可能影响它的安全性。

Having said that, here’s how to browse securely with Opera:
话以至此，下面是如何使用Opera安全地浏览网络:

第一步：[下载Opera浏览器](http://www.opera.com/download)

第二步：打开它的广告拦截器

![](http://p4.qhimg.com/t01974b8cad520103cb.png)

第三步：打开它的VPN

![](http://p0.qhimg.com/t012aff3474e786f94d.png)

第四步：安装HTTPS Everywhere

当你做完这些，Opera应该看起来这样：

![](http://p0.qhimg.com/t011e259e94363bcada.png)

很快-你现在可以放心的浏览网页，你的ISP-或其他任何人-不知道你是谁，也不知道你在做什么。

![](http://p0.qhimg.com/t01270a1712271fde5b.png)

你甚至可以设置你的VPN在不同的国家。这里，我设置我的VPN在新加坡，这样我浏览的网站就会以为我在新加坡。为了测试是否工作，我访问[ipleak.net](https://ipleak.net/)这里显示我的网络地址确实是新加坡。

![](http://p0.qhimg.com/t0118e7c5d19008925e.png)

由于互联网是复杂的，并且数据会通过数百个提供者由[一个对等与交易流量的系统](https://medium.freecodecamp.com/inside-the-invisible-war-for-the-open-internet-dd31a29a3f08)完成通信, 当流量从新加坡发出后，美国的ISP不能够监视此时的流量。

如果你想升级操作，你可以试试Tor浏览器，它非常私有，非常难以破解匿名(虽然这是可以做到的，[在电视节目Mr. Robot](https://medium.freecodecamp.com/all-i-really-need-to-know-about-infosec-i-learned-from-mr-robot-7902cca6d729#.nhwv27j9v)  - 虽然它需要非常非常多的资源来这么做)

Tor有更多的工作要设置和使用，比使用VPN要慢一些。如果你想了解更多，我有一本[入门指南](https://medium.freecodecamp.com/tor-signal-and-beyond-a-law-abiding-citizens-guide-to-privacy-1a593f2104c3#.rouhl2kbf)。

### VPN 服务

人们最常见的方式是通过每月获得VPN服务。有很多这样的服务提供。最终，您必须信任运行VPN的公司，因为没有办法知道他们在使用您的数据。

正如我所说，一些VPN配置不当，可能是泄漏的个人识别数据。

在你购买VPN之前，先在[这里](https://thatoneprivacysite.net/vpn-comparison-chart/)看看它与其他的比较。一旦你买了一个VPN，仔细检查它的是否正常工作，最好的办法是去[ ipleak.net](https://ipleak.net/)然后再使用VPN。

尽管大部分VPN的使用者是公司的远程员工，[如果你购买VPN，NSA会将你记录在名单上](https://www.wired.com/2014/07/nsa-targets-users-of-privacy-services/)。所以我建议使用匿名的东西来购买，比如预加载的VISA卡(顺便说一句，[比特币不是匿名的](https://bitcoin.org/en/you-need-to-know)。)

有几十个VPN服务，但没有明确的“赢家”。我使用$40每年的[私有网络接入](https://www.privateinternetaccess.com/)为家用的计算机和电话提供网络服务。

我也在Twitter上询问他们使用什么VPN，得到了很多回答:

![](http://p0.qhimg.com/t01e411329038f4074a.jpg)

![](https://i.embed.ly/1/display/resize?url=https%3A%2F%2Fpbs.twimg.com%2Fprofile_images%2F835222955592413185%2FPD15eKVL_bigger.jpg&key=4fce0568f2ce49e8b54624ef71a8a5bd&width=40)![](https://i.embed.ly/1/display/resize?url=https%3A%2F%2Fpbs.twimg.com%2Fprofile_images%2F845193361719934976%2FTCsSd6wH_bigger.jpg&key=4fce0568f2ce49e8b54624ef71a8a5bd&width=40)![](https://i.embed.ly/1/display/resize?url=https%3A%2F%2Fpbs.twimg.com%2Fprofile_images%2F644240889846501376%2FDhUW_jKO_bigger.jpg&key=4fce0568f2ce49e8b54624ef71a8a5bd&width=40)![](http://p0.qhimg.com/t01c34397064694552a.png)![](http://p0.qhimg.com/t010f73995aa1f5d4a4.jpg)![](https://i.embed.ly/1/display/resize?url=https%3A%2F%2Fpbs.twimg.com%2Fprofile_images%2F831874683985395712%2FLcTUk8Sd_bigger.jpg&key=4fce0568f2ce49e8b54624ef71a8a5bd&width=40)

### 路由内嵌的VPN

你可以购买内置VPN的路由器。请注意，这些功能并不是专门用来保护您不被ISP窥探的。它们的设计是为了使公司的卫星办公室能够与总部办公室共享同一网络。我以前没用过，所以我不能证明他们的效果。

如果你刚好在美国以外有一个住所，你可以直接接通那个住所的网络。否则，你就需要用我之前提到的VPN服务来配置路由器。

有些路由器的设计在VPN速度上更加有优势。如果你想在路由器层面使用VPN，并且你的网络速度在100 m/s一下，[这款路由器](http://amzn.to/2nPUsMU)可能足够使用了。否则，你就要使用像[这款路由器](http://amzn.to/2n1JLTB)一样更加昂贵的路由器。

如果你不信任路由器公司，你可以使用[Tomato USB](https://en.wikipedia.org/wiki/Tomato_%28firmware%29)来刷新路由器系统。它是另一种基于Linux的开源路由器固件，与一些现成的路由器兼容。

### 保护隐私很困难。但付出是值得的。

隐私权是基本的人权，并且得到[联合国的认可](http://www.un.org/en/universal-declaration-human-rights/)。

现在，有许多人相信我们生活在一个“后隐私时代”。例如，马克·扎克伯格认为隐私权不再那么重要了。但是看看他的行动。他花了三千万刀在帕洛阿尔托附近买了四座房子，这样[他就有更多隐私](http://www.businessinsider.com/mark-zuckerberg-buys-4-homes-for-privacy-2013-10)。

其他人震惊于我们周围的所有数据泄露情况，相信隐私仍然值得争取。

但是大多数人没有真正考虑过就说他们不再关心自己的隐私。

> “Arguing that you don’t care about the right to privacy because you have nothing to hide is no different than saying you don’t care about free speech because you have nothing to say.” — Edward Snowden
> “说你不在乎隐私权，因为你没有什么可隐瞒的，跟你说你不在乎言论自由没什么两样，因为你没什么要说的。”-爱德华·斯诺登

上周的美国参议院投票是一系列事件中最新的一次，表明我们不能信任政府在消费者隐私方面站在消费者一方而采取行动。

我们需要法律赋予更强有力的隐私保护。

我们在注意自己保护隐私的同时，也教育别人这样做。

我建议你阅读计算机安全专家布鲁斯·施奈尔的书“[数据和机械娃娃：隐形的战斗来收集你的数据和控制你的世界](http://amzn.to/2mjheuO).”我从中学到了很多，正在阅读第二遍。

[**Data and Goliath: The Hidden Battles to Capture Your Data and Control Your World**
_Edit description_amzn.to](http://amzn.to/2mjheuO "http://amzn.to/2mjheuO")[](http://amzn.to/2mjheuO)
[**数据和机械娃娃：隐形的战斗来收集你的数据和控制你的世界**
当当网链接](http://product.dangdang.com/1122706281.html "http://product.dangdang.com/1122706281.html")[](http://product.dangdang.com/1122706281.html)

感谢阅读，从现在开始重视隐私。
                
                       

> 英文原文：https://medium.freecodecamp.org/how-to-set-up-a-vpn-in-5-minutes-for-free-and-why-you-urgently-need-one-d5cdba361907
