---
title: DOM
date: 2018-04-15 19:12:29
tags:
---
#### 1.什么是DOM
把文档（document）变成对象（object）的模型（model）；
Node 分为 Document（html）、Element（元素）和 Text（文本）
- Element
title script h1等
- text
指对象中的文本
- document
html由document来生成
- node
node 是原型链的顶端，是上面三个的祖先
![image.png](https://upload-images.jianshu.io/upload_images/11007474-a970b0ebd4672dec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)
注释就是comment
node属于object.prototype
页面中的阶段通过上面的构造函数构造出对应的对象，这就是DOM的主要功能
只有svg的node.name是小写的其他的元素的node.name都是大写
- node.type
1就是element
3就是text

- #####innertext与textcontent的区别
Internet Explorer 引入了`node.innerText`。意图类似，但有以下区别：

*   **`textContent`** 会获取所有元素的内容，包括 [`<script>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/script "HTML <script> 元素用于嵌入或引用可执行脚本。") 和 [`<style>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/style "HTML的<style>元素包含了文档的样式化信息或者文档的一部分。指定的样式化星系包含的该元素内，通常是CSS的格式。") 元素，然而 **innerText **不会。
*   innerText意识到样式，并且不会返回隐藏元素的文本，而textContent会。
*   由于 `innerText` 受 CSS 样式的影响，它会触发重排（reflow），但`textContent` 不会。
*   `与 textContent 不同的是`, 在 Internet Explorer (对于小于等于 IE11 的版本) 中对 innerText 进行修改， 不仅会移除当前元素的子节点，而且还会永久性地破坏所有后代文本节点（所以不可能再次将节点再次插入到任何其他元素或同一元素中）。
- nodeType
只读属性 Node.nodeType 表示的是该节点的类型
**`nodeType`** 属性可用来区分不同类型的节点，比如 [`元素`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element "Element（元素）接口是 Document的一个对象. 这个接口描述了所有相同种类的元素所普遍具有的方法和属性。 这些继承自Element并且增加了一些额外功能的接口描述了具体的行为. 例如,  HTMLElement 接口是所有HTML元素的基础接口， 而 SVGElement 接口是所有SVG元素的基本接口."), [`文本`](https://developer.mozilla.org/zh-CN/docs/Web/API/Text "The Text interface represents the textual content of Element or Attr.  If an element has no markup within its content, it has a single child implementing Text that contains the element's text.  However, if the element contains markup, it is parsed into information items and Text nodes that form its children.") 和 [`注释`](https://developer.mozilla.org/zh-CN/docs/Web/API/Comment "Comment 接口代表标签（markup）之间的文本符号（textual notations）。尽管它通常不显示出来，但是在查看源码里面可以看到。在 HTML 和 XML 里，注释（Comments）为 '<!--' 和 '-->' 之间的内容。在 XML 里，字符序列 '--' 不能用于一个注释中。")

| 常量 | 值 | 描述 |
| --- | --- | --- |
| `Node.ELEMENT_NODE` | `1` | 一个 [`元素`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element "Element（元素）接口是 Document的一个对象. 这个接口描述了所有相同种类的元素所普遍具有的方法和属性。 这些继承自Element并且增加了一些额外功能的接口描述了具体的行为. 例如,  HTMLElement 接口是所有HTML元素的基础接口， 而 SVGElement 接口是所有SVG元素的基本接口.") 节点，例如 [`<p>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p "HTML <p>元素（或者说 HTML 段落元素）表示文本的一个段落。该元素通常表现为一整块与相邻文本分离的文本，或以垂直的空白隔离或以首行缩进。另外，<p> 是块级元素。") 和 [`<div>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/div "HTML <div> 元素 (或 HTML 文档分区元素) 是一个通用型的流内容容器，它在语义上不代表任何特定类型的内容，它可以被用来对其它元素进行分组，一般用于样式化相关的需求（使用 class 或 id 特性) 或者对具有相同特性的一组元素进行分组 (比如 lang)，它应该在没有任何其它语义元素可用时才使用 (比如 <article> 或 <nav>) 。")。 |
| `Node.TEXT_NODE` | `3` | [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element "Element（元素）接口是 Document的一个对象. 这个接口描述了所有相同种类的元素所普遍具有的方法和属性。 这些继承自Element并且增加了一些额外功能的接口描述了具体的行为. 例如,  HTMLElement 接口是所有HTML元素的基础接口， 而 SVGElement 接口是所有SVG元素的基本接口.") 或者 [`Attr`](https://developer.mozilla.org/zh-CN/docs/Web/API/Attr "该类型使用对象来表示一个DOM元素的属性。在大多数DOM方法中，你可能会直接通过字符串的方式获取属性值（例如Element.getAttribute()），但是一些函数（例如Element.getAttributeNode()）或通过迭代器访问时则返回Attr类型。") 中实际的  [`文字`](https://developer.mozilla.org/zh-CN/docs/Web/API/Text "The Text interface represents the textual content of Element or Attr.  If an element has no markup within its content, it has a single child implementing Text that contains the element's text.  However, if the element contains markup, it is parsed into information items and Text nodes that form its children.") |
| `Node.PROCESSING_INSTRUCTION_NODE` | `7` | 一个用于XML文档的 [`ProcessingInstruction`](https://developer.mozilla.org/zh-CN/docs/Web/API/ProcessingInstruction "此页面仍未被本地化, 期待您的翻译!") ，例如 `<?xml-stylesheet ... ?>` 声明。 |
| `Node.COMMENT_NODE` | `8` | 一个 [`Comment`](https://developer.mozilla.org/zh-CN/docs/Web/API/Comment "Comment 接口代表标签（markup）之间的文本符号（textual notations）。尽管它通常不显示出来，但是在查看源码里面可以看到。在 HTML 和 XML 里，注释（Comments）为 '<!--' 和 '-->' 之间的内容。在 XML 里，字符序列 '--' 不能用于一个注释中。") 节点。 |
| `Node.DOCUMENT_NODE` | `9` | 一个 [`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document "Document 接口提供了一些在浏览器服务中作为页面内容入口点而加载的一些页面，也就是 DOM 树。 DOM 树包括诸如 <body> 和 <table> 之类的元素，及其他元素。其也为文档（document）提供了全局性的函数，例如获取页面的 URL、在文档中创建新的 element 的函数。") 节点。 |
| `Node.DOCUMENT_TYPE_NODE` | `10` | 描述文档类型的 [`DocumentType`](https://developer.mozilla.org/zh-CN/docs/Web/API/DocumentType "DocumentType 接口 表示了一个包含文档类型的节点 Node .") 节点。例如 `<!DOCTYPE html>`  就是用于 HTML5 的。 |
| `Node.DOCUMENT_FRAGMENT_NODE` | `11` | 一个 [`DocumentFragment`](https://developer.mozilla.org/zh-CN/docs/Web/API/DocumentFragment "DocumentFragment 接口表示一个没有父级文件的最小文档对象。它被当做一个轻量版的 Document 使用，用于存储已排好版的或尚未打理好格式的XML片段。最大的区别是因为DocumentFragment不是真实DOM树的一部分，它的变化不会引起DOM树的重新渲染的操作(reflow) ，且不会导致性能等问题。") 节点 |

1、3要特别注意

#### 2.函数的属性（方法）
- appendChild()
把一个元素当做另一个元素的儿子
- cloneNode()
（true）就是深拷贝，（false）就是浅拷贝
拷贝，拷贝分为深拷贝和浅拷贝
浅拷贝只复制一层对象的属性，而深拷贝则递归复制了所有层级。
isSameNode与isEquaNode的区别
isSameNode是两个真的是一模一样
isEquaNode是两个看起来一模一样
- nextSibling与preventSibling
[`Node.previousSibling`](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/previousSibling "返回当前节点的前一个兄弟节点,没有则返回null.") 之类的方法可能会引用到一个空白符文本节点, 而不是使用者所预期得到的节点
nextSibling返回当前节点的前一个兄弟节点,没有则返回null.

- removeChild
只是移到内存中，并不是直接删除掉
- normalize()
当前节点和它的后代节点”规范化“（normalized）。在一个"规范化"后的DOM树中，不存在一个空的文本节点，或者两个相邻的文本节点。
注1：“空的文本节点”并不包括空白字符(空格，换行等)构成的文本节点。
注2：两个以上相邻文本节点的产生原因包括：
通过脚本调用有关的DOM接口进行了文本节点的插入和分割等。
HTML中超长的文本节点会被浏览器自动分割为多个相邻文本节点。
```
var wrapper = document.createElement("div");

wrapper.appendChild(document.createTextNode("Part 1 "));
wrapper.appendChild(document.createTextNode("Part 2 "));

// 这时(规范化之前),wrapper.childNodes.length === 2
// wrapper.childNodes[0].textContent === "Part 1 "
// wrapper.childNodes[1].textContent === "Part 2 "

wrapper.normalize();
// 现在(规范化之后), wrapper.childNodes.length === 1
// wrapper.childNodes[0].textContent === "Part 1 Part 2"
```

####3.Document
body
characterSet 字符编码
childElementCount 子标签的数量
children
doctype
documentElement 返回一个文档对象的根元素
domain
fullscreen
head 
hidden 
images 
links 获取所有的a标签
location 
onxxxxxxxxx 事件监听
origin
plugins 查看是否装了flash插件
readyState 引荐 HTTP服务器
referrer
scripts
scrollingElement 正在滚动的元素
styleSheets
title
visibilityState 用户是不是在显示当前
- 方法：
close()
createDocumentFragment()
createElement()
createTextNode()
execCommand() 执行命令 富文本时用
exitFullscreen() 退出全屏
getElementById()
getElementsByClassName()
getElementsByName()
getElementsByTagName() 
getSelection() 选中的文本
hasFocus()
open()
querySelector() 
querySelectorAll()
registerElement()
write() 写
writeln() 写一行

DOM API 获取的elements都是伪数组，没有数组的共有属性的都是伪数组

#### 4.[Element 的接口](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 点击查看
