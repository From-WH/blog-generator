---
title: 前端面试必考篇—HTML
date: 2018-07-08 14:09:19
tags:
---
### 1.（必考） 你是如何理解 HTML 语义化的？

*   答案1：

    *   描述： 标题使用 `h1-h6`，头部用 `header` ，段落用`p`，边栏用`aside`，主要内容用 `main` ，以及 `nav`, `footer` 标签等
    *   原则： 根据内容的结构化（内容语义化），选择合适的标签（代码语义化）**便于开发者阅读**和**写出更优雅的代码**的同时让**浏览器的爬虫和机器很好地解析**。
    *   为什么要进行语义化？
        *   **为了结构清晰** ，在没有CSS的情况下，页面也能呈现出很好地内容结构、代码结构
        *   **提高用户体验**用户体验：例如title、alt用于解释名词或解释图片信息、label标签的活用；
        *   **有利于[SEO](http://baike.baidu.com/view/1047.htm)**：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：[爬虫](http://baike.baidu.com/view/998403.htm)依赖于标签来确定上下文和各个关键字的权重；
        *   **方便其他设备解析**（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
        *   **增强可读性，便于团队开发和维护**。语义化更具可读性，是下一步吧网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化。
*   答案2

    *   `table` 布局的弊端 PHP 后端写 HTML，不会 CSS，于是就用 table 来布局。table 使用展示表格的。严重违反了 HTML 语义化。

    *   `DIV+CSS` 布局的使用 后来有了专门的写 CSS 的前端，他们会使用 DIV + CSS 布局，主要是用 float 和绝对定位布局。稍微符合了 HTML 语义化。

    *   前端专业化 再后来，前端专业化，知道 HTML 的各个标签的用法，于是会使用恰当的标签来展示内容，而不是傻傻的全用 div，会尽量使用 h1、ul、p、main、header 等标签

### 2.meta viewport 是做什么用的，怎么写？

*   具体写法：

    ```
text-html-basic
    <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    ```

*   [原理](https://developer.mozilla.org/zh-CN/docs/Mobile/Viewport_meta_tag)

*   描述： ​ 一开始，所有页面都是给PC准备的，乔布斯推出 iPhone 3GS，页面是不适应手机屏幕的，所以乔布斯的工程师想了一个办法，默认把手机模拟成 980px，页面缩小。

    ​ 后来，智能手机普及，这个功能在部分网站不需要了，所以我们就用 meta:vp 让手机不要缩小我的网页。


### 3.  canvas 元素是干什么的？和 `svg` 的区别是什么？

- `Canvas`

* 含义： ​ 可缩放矢量图形（Scalable Vector Graphics，SVG)，是一种用来描述二维矢量图形的XML 标记语言。 **简单地说，SVG面向图形，HTML面向文本。** ​ `canvas` 是HTML5中新增一个HTML5标签与操作 `canvas` 的 `javascript API`，它可以实现在网页中完成动态的2D与3D图像技术。标记和 SVG以及 VML 之间的一个重要的不同是，有一个基于 JavaScript 的绘图 API，而 SVG 和 VML 使用一个 XML 文档来描述绘图。SVG 绘图很容易编辑与生成，但功能明显要弱一些。 canvas可以完成动画、游戏、图表、图像处理等原来需要Flash完成的一些功能。
*   使用：
最适合图像密集型的游戏，其中的许多对象会被频繁重绘

 我的项目，用到了 canvas 的哪些 `API` ？

参考 MDN 的 canvas [入门手册13](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API)。


-  `SVG`

    *   含义 SVG可缩放矢量图形（Scalable Vector Graphics）是基于可扩展标记语言（XML），用于描述二维矢量图形的一种图形格式。SVG是W3C("World Wide Web ConSortium" 即 " 国际互联网标准组织")在2000年8月制定的一种新的二维矢量图形格式，也是规范中的网络矢量图形标准。SVG严格遵从XML语法，并用文本格式的描述性语言来描述图像内容，因此是一种和图像分辨率无关的矢量图形格式。SVG于2003年1月14日成为 W3C 推荐标准。

    *   特点：

        *   任意放缩

        用户可以任意缩放图像显示，而不会破坏图像的清晰度、细节等。

        *   文本独立

        SVG图像中的文字独立于图像，文字保留可编辑和可搜寻的状态。也不会再有字体的限制，用户系统即使没有安装某一字体，也会看到和他们制作时完全相同的画面。

        *   较小文件

        总体来讲，SVG文件比那些GIF和JPEG格式的文件要小很多，因而下载也很快。

        *   超强显示效果

        SVG图像在屏幕上总是边缘清晰，它的清晰度适合任何屏幕分辨率和打印分辨率。

        *   超级颜色控制

        SVG图像提供一个1600万种颜色的调色板，支持ICC颜色描述文件标准、RGB、线X填充、渐变和蒙版。

        *   交互X和智能化。SVG面临的主要问题一个是如何和已经占有重要市场份额的矢量图形格式Flash竞争的问题，另一个问题就是SVG的本地运行环境下的厂家支持程度。

        浏览器支持： Internet Explorer9，火狐，谷歌Chrome，Opera和Safari都支持SVG。 IE8和早期版本都需要一个插件 - 如Adobe SVG浏览器，这是免费提供的。

    *   二者区别：[SVG与Canvas](https://www.jianshu.com/p/2cb075c858d4)

        [![区别](http://upload-images.jianshu.io/upload_images/11007474-4920a599c19a7d77?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)](https://camo.githubusercontent.com/47f0c36ff73bf923ab934489e9afdcbbc6383fbd/68747470733a2f2f692e6c6f6c692e6e65742f323031382f30332f32352f356162373564613637646133382e706e67) 

    ​

参考链接：

*   [什么是HTML语义化？](http://www.cnblogs.com/freeyiyi1993/p/3615179.html)
*   [HTML语义化](https://segmentfault.com/a/1190000005626375)
*   [移动前端开发之viewport的深入理解](http://www.cnblogs.com/2050/p/3877280.html)
*   [svg](https://www.zhihu.com/question/52819400/answer/308075189)

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/%E9%9D%A2%E8%AF%95%E7%BB%BC%E5%90%88/%E5%89%8D%E7%AB%AF%E9%9D%A2%E8%AF%95%E5%BF%85%E8%80%83%E9%A2%98.md#css)

