---
title: 前端面试必考篇—HTTP
date: 2018-07-10 23:18:56
tags:
---
1.  HTTP 状态码知道哪些？
2.  301 和 302 的区别是什么？
    1.  301 永久重定向，浏览器会记住
    2.  302 临时重定向
3.  HTTP 缓存怎么做？
    1.  Cache-Control: max-age=300
    2.  [http://cdn.com/1.js?v=14](http://cdn.com/1.js?v=1) 避开缓存
4.  Cache-Control 和 Etag 的区别是什么？
5.  Cookie 是什么？Session 是什么？
    *   Cookie
        1.  HTTP响应通过 Set-Cookie 设置 Cookie
        2.  浏览器访问指定域名是必须带上 Cookie 作为 Request Header
        3.  Cookie 一般用来记录用户信息
    *   Session
        1.  Session 是服务器端的内存（数据）
        2.  Session 一般通过在 Cookie 里记录 SessionID 实现
        3.  SessionID 一般是随机数
6.  LocalStorage 和 Cookie 的区别是什么？
    1.  Cookie 会随请求被发到服务器上，而 LocalStorage 不会
    2.  Cookie 大小一般4k以下，LocalStorage 一般5Mb 左右
7.  （必考）GET 和 POST 的区别是什么？
    1.  参数。GET 的参数放在 url 的查询参数里，POST 的参数（数据）放在请求消息体里。
    2.  安全（扯淡）。GET 没有 POST 安全（都不安全）
    3.  GET 的参数（url查询参数）有长度限制，一般是 1024 个字符。POST 的参数（数据）没有长度限制（扯淡，4~10Mb 限制）
    4.  包。GET 请求只需要发一个包，POST 请求需要发两个以上包（因为 POST 有消息体）（扯淡，GET 也可以用消息体）
    5.  GET 用来读数据，POST 用来写数据，POST 不幂等（幂等的意思就是不管发多少次请求，结果都一样。）
8.  （必考）怎么跨域？JSONP 是什么？CORS 是什么？postMessage 是什么？
    1.  JSONP
    2.  CORS
    3.  postMessage 看一下 MDN

## [](https://github.com/Jsmond2016/blog/blob/master/%E5%B7%B2%E5%AE%8C%E6%88%90/%E9%9D%A2%E8%AF%95%E7%BB%BC%E5%90%88/%E5%89%8D%E7%AB%AF%E9%9D%A2%E8%AF%95%E5%BF%85%E8%80%83%E9%A2%98.md#vue)

