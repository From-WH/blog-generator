---
title: CSS学习方法及常用属性
date: 2018-03-23 00:48:34
tags:
---
![image.png](https://upload-images.jianshu.io/upload_images/11007474-67cc62100fae52c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 1.CSS的历史（Cascading Style Sheets 层叠样式表）
- [维基百科](https://zh.wikipedia.org/wiki/%E5%B1%82%E5%8F%A0%E6%A0%B7%E5%BC%8F%E8%A1%A8)

### 2.CSS学习资源
-  Google: 关键词 MDN
-  [CSS Tricks](https://css-tricks.com/ "null")
-  [Google: 阮一峰 css](https://www.google.com/search?q=%E9%98%AE%E4%B8%80%E5%B3%B0+css "null")
-  [张鑫旭的 240 多篇 CSS 博客](http://www.zhangxinxu.com/wordpress/category/css/page/25/ "null")
-  [Codrops 炫酷 CSS 效果](https://tympanus.net/codrops/category/playground/ "null")
-  [CSS揭秘](http://www.ituring.com.cn/book/1695 "null")
-  [CSS 2.1 中文 spec](http://cndevdocs.com/ "null")
-  [Magic of CSS](http://adamschwartz.co/magic-of-css/ "null") 免费在线书
### 3.引入CSS的四种方式
- 内联（style）样式
- style标签方法
- link rel（relationship 关系）外部引入
- 利用@import url 外部CSS再引入CSS
![image.png](https://upload-images.jianshu.io/upload_images/11007474-d353a6c93f34c1a6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4.常见的CSS属性
- 常见的块级元素和行内元素：
块级元素：h/p/div/hr/form/ui/ol/li/dl/dt/dd/pre/table/tr/td/th
行内元素：em/strong/span/a/br/img/buttom/input/label/select/textarea/code/script

- 如何分别让块级元素和行内元素水平居中
对于块级元素
通过设置width:0px; margin： 0px auto;即可实现水平居中
对于行内元素
通过设置在其父元素下设置text-align:center;即可该行内元素实现水平居中
块级元素和行内元素的特性：
块级元素会占用一整行，其他块级元素会被挤下到另一行，而行内元素之间可以在同一行存在
块级元素可以设计长宽，而行内元素无法设置长宽
行内元素设置margin和padding时只有左右有效，上下无效
块级元素可以包含行内元素和块级元素，行内元素只能包含行内元素和文本

### 5.继承
继承是依赖于父子关系的一种机制。对于某个样式应用于某个父元素时，子元素如果不做特别的限制，子元素会继承父元素的一些样式
- 无继承性的属性
1、display：规定元素应该生成的框的类型
2、文本属性：
vertical-align：垂直文本对齐
text-decoration：规定添加到文本的装饰
text-shadow：文本阴影效果
white-space：空白符的处理
unicode-bidi：设置文本的方向
3、盒子模型的属性
4、背景属性
5、定位属性：float、clear、position、top、right、bottom、left、min-width、min-height、max-width、max-height、overflow、clip、z-index
6、生成内容属性：content、counter-reset、counter-increment
7、轮廓样式属性：outline-style、outline-width、outline-color、outline
8、页面样式属性：size、page-break-before、page-break-after
9、声音样式属性：pause-before、pause-after、pause、cue-before、cue-after、cue、play-during
- 可以继承属性
1、字体系列属性
font：组合字体
font-family：规定元素的字体系列
font-weight：设置字体的粗细
font-size：设置字体的尺寸
font-style：定义字体的风格
font-variant：设置小型大写字母的字体显示文本，这意味着所有的小写字母均会被转换为大写，但是所有使用小型大写字体的字母与其余文本相比，其字体尺寸更小。
font-stretch：对当前的 font-family 进行伸缩变形。所有主流浏览器都不支持。
font-size-adjust：为某个元素规定一个 aspect 值，这样就可以保持首选字体的 x-height。
2、文本系列属性
text-indent：文本缩进
text-align：文本水平对齐
line-height：行高
word-spacing：增加或减少单词间的空白（即字间隔）
letter-spacing：增加或减少字符间的空白（字符间距）
text-transform：控制文本大小写
direction：规定文本的书写方向
color：文本颜色
3、元素可见性：visibility
4、表格布局属性：caption-side、border-collapse、border-spacing、empty-cells、table-layout
5、列表布局属性：list-style-type、list-style-image、list-style-position、list-style
6、生成内容属性：quotes
7、光标属性：cursor
8、页面样式属性：page、page-break-inside、windows、orphans
9、声音样式属性：speak、speak-punctuation、speak-numeral、speak-header、speech-rate、volume、voice-family、pitch、pitch-range、stress、richness、、azimuth、elevation

### 6.div
- div的高度及流动
文档流：就是文档内元素的流动方向
内联元素：从左往右流动
块级元素：独占一行，从上往下流动
块级元素的高度由内部文档流元素的高度决定
特殊单词较长的情况 需要word break：break-all； 才会被打断换行
行高字体默认有一个建议行高，不同的字体建议行高不同

### 7.background
- background-size: 设置背景图片大小
contain 或 cover:
保留固有比例，最大的包含或覆盖背景区。如果图像没有固有比例，则按背景区大小
加auto
以背景图片的比例缩放背景图片，最好不要只用一个auto
- background-position 指定背景图片的初始位置
- position 指定一个元素在文档中的定位方式
**定位元素（positioned element）**是其[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `relative`, `absolute`, `fixed `或 `sticky` 的一个元素。
**相对定位元素（**relatively positioned element**）**是[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `relative `的元素。
**绝对定位元素（absolutely positioned element）**是[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `absolute` 或 `fixed` 的元素。
**粘性定位元素**（**stickily positioned element**）**是[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `sticky` 的元素
- max-width 最大宽度

### 8.display的几个常用属性
- `none` 关闭一个元素的显示（对布局没有影响）；其所有后代元素都也被会被关闭显示。文档渲染时，该元素如同不存在要想让元素在隐藏的同时占据其原有的位置
- `inline`  该元素生成一个或多个行内元素盒。
- `block`  该元素生成一个块元素盒。 
- `list-item` 该元素生成一个容纳内容和单独的列表行内元素盒的块状盒。 
- `inline-block`该元素生成一个块状盒，该块状盒随着周围内容流动，如同它是一个单独的行内盒子（表现更像是一个被替换的元素）
**加了dinline-block后一般都要在加一个vertical-align：top；来清除bug**
### 9.伪类
- :nth-child(an+b) 匹配文档树中在其之前具有 an+b-1 个兄弟节点的元素，其中 n 为正值或零值
0n+3 或简单的 3 匹配第三个元素。
1n+0 或简单的 n 匹配每个元素。（兼容性提醒：在 Android 浏览器 4.3 以下的版本 n 和 1n 的匹配方式不一致。1n 和 1n+0 是一致的，可根据喜好任选其一来使用。）
2n+0 或简单的 2n 匹配位置为 2、4、6、8...的元素。你可以使用关键字 even 来替换此表达式。
2n+1 匹配位置为 1、3、5、7...的元素。你可以使用关键字 odd 来替换此表达式。
3n+4 匹配位置为 4、7、10、13...的元素。
：一个冒号是伪类
：：两个冒号是伪元素

---
**单词**
`transition：box-shadow 1s；`过度效果 给谁添加 过程1S
protfolio 作品集
box-sizing: border-box; 使这个盒子的宽度包含margin和padding

