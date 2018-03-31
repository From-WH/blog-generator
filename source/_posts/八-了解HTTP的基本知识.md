---
title: 了解HTTP的基本知识
date: 2018-03-20 22:20:10
tags:
---
###1990年前的历史
上世纪九十年代前，互联网还没有被发明出来，那时候的网络基本以发邮件（Email1965年发明）等形式简单实用
###1990年后的世界
- Tim Berners-Lee（下文中称为李爵士） 在 1989 年至 1992 年间，发明了 WWW（World Wide Web）
- 主要包含三个概念
URI，俗称网址
HTTP，两个电脑之间传输内容的协议
HTML，超级文本，主要用来做页面跳转
URL 的作用是能让你访问一个页面，HTTP 的作用是让你能下载这个页面，HTML 的作用是让你能看懂这个页面
完美搭配干活不累
- 李爵士除了发明了这些概念，还：
发明了第一个服务器
发明了第一个浏览器
写出了第一个网页
**因此他获得了计算机科学领域最富盛名的的奖项——图灵奖**
[万维网之父Tim Berners-Lee获图灵奖：奖金100万美元](http://www.sohu.com/a/132077489_465975)（点击查看获奖信息）
###URI（Uniform Resource Identifier）
是一个用于标识某一互联网资源名称的字符串
URI 分为 URL 和 URN，我们一般使用 URL 作为网址
- URN（统一资源编码）
ISBN: 9787115275790 就是一个 URN，通过 URN 你可以确定一个「唯一的」资源，ISBN: 9787115275790 对应的资源的是《JavaScript 高级程序设计（第三版）》这本书。你去是介绍任何一个图书馆、书店，他们都知道是这本书。
- URL（统一资源定位符）
通过 URL 你可以确定一个【唯一的】地址（网址）
![image.png](https://upload-images.jianshu.io/upload_images/11007474-9b4b4e1e701230ec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800)
一级域名com
二级域名baidu
三级域名www
![image.png](https://upload-images.jianshu.io/upload_images/11007474-fee6efd185027012.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/800
)
www.baidu.com
###DNS
- 输入域名
- 输出IP
##Server + Client + HTTP
浏览器负责发起请求
服务器在 80 端口接收请求
服务器负责返回内容（响应）
浏览器负责下载响应内容
HTTP 的作用就是指导浏览器（Clinet）和服务器（Server）如何进行沟通
**请求示例**
1.`url -s -v -H "Frank: xxx" -- "https://www.baidu.com"`
请求的内容为
```
GET / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
```
2.
`curl -X POST -s -v -H "Frank: xxx" -- "https://www.baidu.com"`
请求的内容为
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
```
请求的格式
```
1 动词 路径 协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3 
4 要上传的数据
```
请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）
第三部分永远都是一个回车（\n）
动词有 `GET POST PUT PATCH DELETE HEAD OPTIONS `等
这里的路径包括「查询参数」，但不包括「锚点」(锚点是浏览器看的，服务器不看)
如果你没有写路径，那么路径默认为 /
第 2 部分中的 Content-Type 标注了第 4 部分的格式
##用 Chrome 发请求
打开 Network
地址栏输入网址
在 Network 点击，查看 request，点击「view source」
点击「view source」
点击「view source」
点击「view source」
终于点了？可以看到请求的前三部分了
如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到
##响应
响应的格式
```
1 协议/版本号 状态码 状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容
```
状态码
状态码要背，是服务器对浏览器说的话
1xx 不常用
2xx 表示成功
3xx 表示滚吧
4xx 表示你丫错了
5xx 表示好吧，我错了
[状态码查询](http://www.runoob.com/http/http-status-codes.html)
##用 Chrome 查看响应
打开 Network
输入网址
选中第一个响应
查看 Response Headers，点击「view source」，点击「view source」，点击「view source」
你会看到响应的前两部分
查看 Response 或者 Preview，你会看到响应的第 4 部分