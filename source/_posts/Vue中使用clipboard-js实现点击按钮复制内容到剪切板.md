---
title: Vue中使用clipboard.js实现点击按钮复制内容到剪切板
date: 2018-07-01 21:12:18
tags:
---
### 需求设定:
1.点击某个按钮，将设置的目标内容(例如下载链接地址)复制到剪切板，可以在电脑上任何地方粘贴
2.不使用任何框架和使用Flash，以最小的代码实现该功能，并能兼容所有主流浏览器
---

###插件选择clipboard.js

1.  官网链接地址：[clipboard.js](https://clipboardjs.com/)
2. 引入方式：
NPM方式：
```
npm install clipboard --save
```
直接引入：下载源代码以后将相关JS放在目录下，之后引入：
```
<script src="xxx/clipboard.min.js"></script>
````

3. 使用方式(官方文档例子)：
- HTML(target包括但不限于input)
```
<!-- Target -->
<input id="foo" value="https://github.com/zenorocha/clipboard.js.git">
<!-- Trigger -->
<button class="btn" data-clipboard-target="#foo">
    点击复制
</button>
```

- JS
```
var clipboard = new ClipboardJS('.btn');
//成功回调
clipboard.on('success', function(e) {
    console.info('Action:', e.action);
    console.info('Text:', e.text);
    console.info('Trigger:', e.trigger);  
    e.clearSelection();
});
//失败回调
clipboard.on('error', function(e) {
    console.error('Action:', e.action);
    console.error('Trigger:', e.trigger);
});
```
