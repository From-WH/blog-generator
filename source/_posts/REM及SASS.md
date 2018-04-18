---
title: REM及SASS
date: 2018-04-18 20:53:01
tags:
---
#### 1.几个常见单位
- 介绍几个单位
em：一个m的宽度，但是面试官喜欢：一个字的宽度，PS：这是错的
px：像素
rem：根元素（html）的font-size是多少REM就是多少
vh：视口的高度
vw：视口的宽度
[更多单位详见](https://developer.mozilla.org/zh-CN/docs/Web/CSS/length)
- 12像素法则
只在chrome里面有效
如果chrome设置了最小字号为12px，那么你设置再小的的字号它还是12px

#### 2.em和rem的区别
rem是指根元素字的大小
em是当前元素设置的字的大小
响应式就是不同屏幕得到不同的样子

##### 3.动态REM
一切以宽度为准，  就能保证完美还原设计
- 首先：
让页面的html的font-size与页面的宽度相等，就是1rem就是一个页面的宽度
- 其次：
所有的单位都用rem，margin啊、width啊，height啊
就是使得页面在布局的时候确定了比例
![image.png](https://upload-images.jianshu.io/upload_images/11007474-82c9b5529e5e9dd4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)

如果觉得CSS里面的rem全是小数不爽的话，就把html的font-size改为页面宽度的十分之一
但是像border、font-size就用px或em，太小了会显示不出来

#### 4.SASS
不会SASS/CASS/Wepake/LESS的原因就是因为：
1.你不会命令行
2.英语不好
3.不会看文档
**怎么安装及使用SASS？**（我的是window）按方方老师教程
在 SCSS 里使用 PX2REM
```
*   npm config set registry [https://registry.npm.taobao.org/](https://registry.npm.taobao.org/ "null")
touch ~/.bashrc
echo 'export SASS_BINARY_SITE="[https://npm.taobao.org/mirrors/node-sass](https://npm.taobao.org/mirrors/node-sass "null")"' >> ~/.bashrc
source ~/.bashrc
npm i -g node-sass
mkdir ~/Desktop/scss-demo
cd ~/Desktop/scss-demo
mkdir scss css
touch scss/style.scss
start scss/style.scss
node-sass -wr scss -o css
```
然后在
    编辑 scss 文件就会自动得到 css 文件
    在 scss 文件里添加

```
    @function px( $px ){
      @return $px/$designWidth*10 + rem;
    }
    $designWidth : 640; // 640 是设计稿的宽度，你要根据设计稿的宽度填写。如果设计师的设计稿宽度不统一，就杀死设计师，换个新的。
    .child{
      width: px(320);
      height: px(160);
      margin: px(40) px(40);
      border: 1px solid red;
      float: left;
      font-size: 1.2em;
    }
```
即可实现 px 自动变 rem