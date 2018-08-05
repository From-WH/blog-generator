---
layout: ajax
title: AJAX小知识
date: 2018-07-12 19:48:18
tags:
---
## 1.如何发请求？

我们知道有几种方式可以发请求，但是都有其局限性，如下：

> 用 form 可以发请求，但是会*刷新页面或新开页面*
> 
> 用 a 可以发 get 请求，但是也会*刷新页面或新开页面*
> 
> 用 img 可以发 get 请求，但是*只能以图片的形式展示*
> 
> 用 link 可以发 get 请求，但是*只能以 CSS、favicon 的形式展示*
> 
> 用 script 可以发 get 请求，但是*只能以脚本的形式运行*

思考：有没有这样的发请求的方式？

> 1.  get、post、put、delete 请求都行
> 2.  想以什么形式展示就以什么形式展示

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#2ajax-%E7%9A%84%E5%87%BA%E7%8E%B0)2.AJAX 的出现

> AJAX即“Asynchronous JavaScript and XML”（异步的JavaScript与XML技术)

### [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#21-ajax-%E7%9A%84%E5%8E%86%E5%8F%B2)2.1 AJAX 的[历史](https://zh.wikipedia.org/zh-hans/AJAX)

*   服务器之殇

    ​ 上个世纪90年代，几乎所有的网站都由HTML页面实现，服务器处理每一个用户请求都需要重新加载网页。这样的处理方式效率不高。用户的体验是所有页面都会消失，再重新载入，即使只是一部分页面元素改变也要重新载入整个页面，不仅要刷新改变的部分，连没有变化的部分也要刷新。这会**加重服务器的负担**。

*   异步加载和iframe方案

    ​ 这可以用**异步加载**来解决。1995年，JAVA语言的第一版发布，随之发布的的Java applets（JAVA小程序）首次实现了异步加载。浏览器通过*运行嵌入网页中的Java applets与服务器交换数据，不必刷新网页*。1996年，Internet Explorer将**iframe元素**加入到HTML，支持局部刷新网页。

*   XMLHttp 的出现

    ​ 1998年前后，Outlook Web Access小组写成了允许客户端脚本发送HTTP请求（**XMLHTTP**）的第一个组件。该组件原属于微软Exchange Server，并且迅速地成为了Internet Explorer 4.0[2]的一部分。部分观察家认为，Outlook Web Access是第一个应用了Ajax技术的成功的商业应用程序，并成为包括Oddpost的网络邮件产品在内的许多产品的领头羊。但是，2005年初，许多事件使得Ajax被大众所接受。Google在它著名的交互应用程序中使用了异步通讯，如Google讨论组、Google地图、Google搜索建议、Gmail等。Ajax这个词由《Ajax: A New Approach to Web Applications》一文所创，该文的迅速流传提高了人们使用该项技术的意识。另外，对Mozilla/Gecko的支持使得该技术走向成熟，变得更为简单易用。

*   总结为：

    > IE 5 率先在 JS 中引入 ActiveX 对象（API），使得 JS 可以直接发起 HTTP 请求。 随后 Mozilla、 Safari、 Opera 也跟进（抄袭）了，取名 XMLHttpRequest，并被纳入 W3C 规范

### [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#22-ajax-%E7%9A%84%E4%BC%98%E7%BC%BA%E7%82%B9)2.2 AJAX 的优缺点

*   优点

    ​ （1）实现局部更新：

    ​ 就是能在不更新整个页面的前提下维护数据。这使得Web应用程序更为迅捷地回应用户动作，并避免了在网络上发送那些没有改变的信息。

    ​ （2）仅依赖于浏览器和JavaScript：

    ​ Ajax不需要任何浏览器插件，但需要用户允许JavaScript在浏览器上执行。就像DHTML应用程序那样，Ajax应用程序必须在众多不同的浏览器和平台上经过严格的测试。随着Ajax的成熟，一些简化Ajax使用方法的程序库也相继问世。同样，也出现了另一种辅助程序设计的技术，为那些不支持JavaScript的用户提供替代功能。

*   缺点

    ​ （1）浏览器的兼容问题：

    ​ Ajax在本质上是一个浏览器端的技术，首先面临无可避免的第一个问题即是浏览器的兼容性问题。各家浏览器对于JavaScript／DOM／CSS的支持总有部分不太相同或是有Bug，甚至同一浏览器的各个版本间对于JavaScript／DOM／CSS的支持也有可能部分不一样。这导致程序员在写Ajax应用时花大部分的时间在调试浏览器的兼容性而非在应用程序本身。因此，目前大部分的Ajax链接库或开发框架大多以js链接库的形式存在，以定义更高阶的JavaScript API、JavaScript对象（模板）、或者JavaScript Widgets来解决此问题。

    ​ （2）局部刷新带来的问题：

    ​ Ajax技术之主要目的在于局部交换客户端及服务器之间的数据。如同传统之主从架构，无可避免的会有部分的业务逻辑会实现在客户端，或部分在客户端部分在服务器。由于业务逻辑可能分散在客户端及服务器，且以不同之程序语言实现，这导致Ajax应用程序极难维护。如有用户接口或业务逻辑之更动需求，再加上前一个JavaScript/DOM/CSS 之兼容性问题，Ajax应用往往变成程序员的梦魇。

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#3ajax-%E7%9A%84-%E4%BD%BF%E7%94%A8)3.AJAX 的 [使用](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)

### [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#31-ajax%E7%9A%84%E5%8E%9F%E7%90%86)3.1 AJAX的原理

1.  使用 XMLHttpRequest 发请求
2.  服务器返回 XML 格式的字符串
3.  JS 解析 XML，并更新局部页面

### [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#32-ajax--%E7%9A%84%E7%9B%AE%E7%9A%84)3.2 AJAX 的目的：

> 使用 js 发请求 ，使用 js 处理返回的响应。

### [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#33-%E8%AF%B7%E7%94%A8%E5%8E%9F%E7%94%9F-js%E5%86%99%E5%87%BA%E4%B8%80%E4%B8%AAajax%E8%AF%B7%E6%B1%82)3.3 请用原生 JS写出一个AJAX请求：

```text-html-basic
<body>
	<button id="button">点我</button>
	<script>
		button.addEventListener('click',(e)=>{
			let request = new  XMLHttpRequest()
			request.open(method,address)
			request.send()
			reqeust.onreadychange() = ()={
				if(request.readyState === 4){
					if(request.status >= 200 && reuest.status<  300){
						let string = esponseText
						let object =window.JSON.parse(string) 
					}
				}
			}

		})
	</script>
</body>
```

分析：

*   `let request = new XMLHttpRequest()` 创建一个AJAX实例

*   `request.open(method,address)` 初始化请求，一般有3个参数 ，如果没有设置就是 默认值`request.open(method,url,async)`

    *   `method` ：请求的类型；GET 或 POST
    *   `url` ： 文件在服务器上的位置
    *   `async` ：true（异步）或 false（同步）
*   `request.send()` 发送请求(如果参数为String，只能为 post请求)

*   `reqeust.onreadychange()` 监听 `readystatue` 的变化 ，每当 readyState 改变时，就会触发 onreadystatechange 事件。

    *   `request.readyState` XMLHttpRequest 的状态。从 0 到 4 发生变化

| 值 | readyState 状态 | 意义 |
| --- | --- | --- |
| 0 | `UNSENT`(未打开) | `open()`方法还未被调用，请求未初始化 |
| 1 | `OPENED` (未发送) | `open()`方法已经被调用， 服务器连接已建立 |
| 2 | HEADERS_RECEIVED (已获取响应头) | `send()`方法已经被调用, 响应头和响应状态已经返回.请求已接收 |
| 3 | LOADING (正在下载响应体) | 响应体下载中; `responseText`中已经获取了部分数据. |
| 4 | DONE (请求完成) | 整个请求过程已经完毕. |

        *   `request.status` 200表示OK；404表示未找到页面。

### [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/AJAX/AJAX%E5%B0%8F%E7%9F%A5%E8%AF%86.md#34-%E6%B5%8F%E8%A7%88%E5%99%A8%E6%98%AF%E5%85%88%E4%B8%8B%E8%BD%BD%E5%85%A8%E9%83%A8%E5%86%85%E5%AE%B9%E5%86%8D%E5%88%A4%E6%96%AD%E6%88%90%E5%8A%9F%E5%92%8C%E5%A4%B1%E8%B4%A5%E5%90%97)3.4 浏览器是先下载全部内容再判断成功和失败吗？

答：

不是的，从上面的HTTP响应的返回值我们知道，发送给浏览器（客户端）的响应是先发送响应头`responseHeader` ，判断之前的请求成功与失败，然后再进行下载。

同时，因为响应的内容[大小有限制](http://blog.csdn.net/yaopeng_2005/article/details/6706739)，每次传输数据有限而分次传输，因此是先判断 ，后下载完成。

参考文章：

​ [Ajax 入门简介](https://www.ibm.com/developerworks/cn/xml/wa-ajaxintro1.html)

​ [AJAX-阮一峰](http://javascript.ruanyifeng.com/bom/ajax.html)

​ [为什么form表单提交没有跨域问题，但ajax提交有跨域问题？](https://www.zhihu.com/question/31592553)

​ [XMLHttpRequest-MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)

​ [AJAX-MDN](https://developer.mozilla.org/zh-CN/docs/Web/Guide/AJAX)

