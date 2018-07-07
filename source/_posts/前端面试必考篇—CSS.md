---
title: 前端面试必考篇—CSS
date: 2018-07-07 23:12:27
tags:
---
1.  （必考） 说说盒模型。

    *   举例：
 content-box: width == 内容区宽度 border-box: width == 内容区宽度 + padding 宽度 + border 宽度 （不管 IE *{box-sizing: border-box;}）

2.  css reset 和 normalize.css 有什么区别？

    *   考英文：
        *   reset 重置，之前的样式我不要，a{color: red;}，抛弃默认样式
        *   normalize 让所有浏览器的标签都跟**标准规定的默认样式一致**，各浏览器上的标签默认样式基本统一。
3.  （必考）如何居中？

    *   平时总结：
        *   水平居中：

            *   内联：爸爸身上写 text-align:center;

            *   块级：margin-left: auto; margin-right: auto;

                > margin-left:auto;margin-right:auto;和margin:0 auto;的区别
                > 
                > [避免前面的元素的样式被后面的元素样式所覆盖](http://www.imooc.com/qadetail/93736)

        *   垂直居中：

            *   [七种方式实现垂直居中](https://jscode.me/t/topic/1936)
            *   [CSS 元素垂直居中的 6种方法](https://blog.csdn.net/wolinxuebin/article/details/7615098)
4.  选择器优先级如何确定？

    1.  选择器越具体，优先级越高。 #xxx 大于 .yyy
    2.  同样优先级，写在后面的覆盖前面的。
    3.  color: red !important; 优先级最高。
5.  BFC 是什么？

    *   举例：
        *   overflow:hidden 清除浮动。（方方总是用 .clearfix 清除浮动，坚决不用 overflow:hidden 清除浮动）
        *   overflow:hidden 取消父子 margin 合并。[http://jsbin.com/conulod/1/edit?html,css,js,output4](http://jsbin.com/conulod/1/edit?html,css,js,output) （方方用 padding-top: 1px;）
6.  如何清除浮动？

    1.  overflow: hidden （方方反对）

    2.  .clearfix 清除浮动写在爸爸身上

        ```
        .clearfix::after{
            content: ''; display: block; clear:both;
        }
        .clearfix{
            zoom: 1; /* IE 兼容 */
        }

        ```

