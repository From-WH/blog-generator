---
title: 三.VSCode安装及配置
date: 2018-03-20 22:12:58
tags:
---
# VSCode
- **安装** 
1.从官网下载安装包
安装时把以下选项选中：
![image.png](https://upload-images.jianshu.io/upload_images/11007474-3443031529a7f112.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
- **使用** 
1.找个地方新建一个目录（目录名不要中文），假设目录名为 vs-demo
2.右键点击该目录，open with code
3.使用 Ctrl+Shift+E 打开资源管理器，在 vs-demo 目录里新建 HTML 文件，文件名为 index.html
4.在 index.html 依次输入：英文感叹号、<kbd>回车</kbd> 键，即可看到一个完整的 HTML 页面
这种快捷写法叫做 Emmet，目前所有的前端编辑器都支持 Emmet。
[Emmet作弊表](https://docs.emmet.io/cheat-sheet/)
- **配置**
VSCode 的配置方式就写编辑一个配置文件，打开「文件 - 首选项 - 设置」，对应快捷键为 <kbd>Ctrl</kbd> + <kbd>,</kbd>
左侧为系统默认配置项，右侧为你要覆盖的配置项。把你要修改的项从左边拷贝到右边，然后保存，即可生效。
- **设置字体与字号**
首先：笔者个人觉得默认就挺好，如果不喜欢可以自行设置：
在上面配置中,在右侧文件中添加一行（注意末尾要有英文逗号）
`"editor.fontSize": 18,`
保存，字号就变大了。
设置字体也是类似，添加
`"editor.fontFamily": "Consolas, 'Courier New', monospace",`
即可将字体设置为你想要的。
- **安装插件**
VSCode 自带 Emmet、Git 继承和 JS 调试功能
**安装 open in browser**
按 Ctrl + Shift + X 打开扩展面板，然后输入 open in browser，点击第一个结果的「安装」按钮，稍等片刻就安装好了。
安装好后，就可以在编辑栏右键点击直接使用默认浏览器进行查看。
*待续*