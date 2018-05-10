---
title: Session、LocatStorage、Cache-Control、ETag
date: 2018-05-10 19:36:22
tags:
---
### cookie与session有什么区别？

1. 由于HTTP协议是无状态的协议，所以服务端需要记录用户的状态时，就需要用某种机制来识具体的用户，这个机制就是Session.典型的场景比如购物车，当你点击下单按钮时，由于HTTP协议无状态，所以并不知道是哪个用户操作的，所以服务端要为特定的用户创建了特定的Session，用用于标识这个用户，并且跟踪用户，这样才知道购物车里面有几本书。这个Session是保存在服务端的，有一个唯一标识。在服务端保存Session的方法很多，内存、数据库、文件都有。集群的时候也要考虑Session的转移，在大型的网站，一般会有专门的Session服务器集群，用来保存用户会话，这个时候 Session 信息都是放在内存的，使用一些缓存服务比如Memcached之类的来放 Session。
2. 思考一下服务端如何识别特定的客户？这个时候Cookie就登场了。每次HTTP请求的时候，客户端都会发送相应的Cookie信息到服务端。实际上大多数的应用都是用 Cookie 来实现Session跟踪的，第一次创建Session的时候，服务端会在HTTP协议中告诉客户端，需要在 Cookie 里面记录一个Session ID，以后每次请求把这个会话ID发送到服务器，我就知道你是谁了。有人问，如果客户端的浏览器禁用了 Cookie 怎么办？一般这种情况下，会使用一种叫做URL重写的技术来进行会话跟踪，即每次HTTP交互，URL后面都会被附加上一个诸如 sid=xxxxx 这样的参数，服务端据此来识别用户。
3. Cookie其实还可以用在一些方便用户的场景下，设想你某次登陆过一个网站，下次登录的时候不想再次输入账号了，怎么办？这个信息可以写到Cookie里面，访问网站的时候，网站页面的脚本可以读取这个信息，就自动帮你把用户名给填了，能够方便一下用户。这也是Cookie名称的由来，给用户的一点甜头。所以，总结一下：Session是在服务端保存的一个数据结构，用来跟踪用户的状态，这个数据可以保存在集群、数据库、文件中；Cookie是客户端保存用户信息的一种机制，用来记录用户的一些信息，也是实现Session的一种方式。

### 什么是session？
服务器通过cookie给用户一个sessionID，
sessionID对应服务器里的一小块内存，
每次用户访问服务器的时候，服务器就通过sessionID去读取对应的session，来知道用户的隐私信息
- 面试的时候怎么回答cookie和session的特点：
![image.png](https://upload-images.jianshu.io/upload_images/11007474-826f23f222850543.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/840)


### localStorage是什么
是html5技术提供的一个API，
session是服务器上的哈希表
localStorage的实质就是一个哈希表，是浏览器上的哈希表
- `localStorage.setItem()` 接受两个参数，可以存一个key、value，只能以字符串的形式存
如果要存一个对象，可以用JSON.stringify进行转化
- `localStorage.getItem()` 可以获取值，只接受一个name
- `localStorage.clear()` 不接受参数，清空key、value
都是用来操作当前页面里面的哈希表

localStorage不存在与页面里，它存在C盘的一个文件里
session的缺点就是占内存
应用：
场景：页面更新，提示用户，但是只提醒一次，用户二次进入（刷新）的时候不需要提示
![image.png](https://upload-images.jianshu.io/upload_images/11007474-4e90160326a6ecca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- localStroage与sessionStroage的区别
![image.png](https://upload-images.jianshu.io/upload_images/11007474-1ce596507f0058d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/740)
sessionStroage与session没有关系



### session与Cookie什么关系
一般来说session是基于Cookie实现的，反过来说cookie是session的基石
以为session必须把sessionID放进cookie里再发送给客户端

session大部分时间是基于Cookie来存储ID的，但是它也可以通过查询参数和localStroage来存储它的ID

### localStroage与Cookie的区别
cookie每次会带给服务器，localStroage不会带给服务器，它与HTTP无关
cookie最大4k，loaclStroage5MB左右

### Cache-Control
HTTP缓存，web优化（常识）
将某文件缓存至本地
`response.setHeather(‘Cache-Control’,'max-age=30')`将文件在本地保留30s，刷新不会请求，30s后刷新重新请求，一般`max-age`要设置久一点例如十年！300000000（阔怕！）
但是，浏览器觉得你存那么久也没啥用，一般一年以后就帮你清了
你问有什么后果吗？
没有！反正也没bug，也就是加载可能慢一点点而已
![image.png](https://upload-images.jianshu.io/upload_images/11007474-42f368948ad72954.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/740)
首页不会使用使用cache-contorl
如果要升级css或js就在后面加上一个查询参数
如`https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js`
更新后：`https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js?v=2`这样的话`max-age=30'`就会失效
- Expires和Cache-Control有什么区别
Expires设置的是时间点
Cache-Control设置的是时间长度
如果同时设置有限使用Cache-Control

Cache-Control是升级后才有的，10几年前都是用Expires控制缓存
`Expires: Wed, 21 Oct 2015 07:28:00 GMT`因为他用的本地时间，如果时间错乱了，那你就完了

### 了解MD5 （讯息摘要算法）
一种被广泛使用的[密码杂凑函数](https://zh.wikipedia.org/wiki/%E5%AF%86%E7%A2%BC%E9%9B%9C%E6%B9%8A%E5%87%BD%E6%95%B8 "密码杂凑函数")，可以产生出一个128位元（16[位元组](https://zh.wikipedia.org/wiki/%E5%AD%97%E8%8A%82 "字节")）的散列值（hash value），用于确保信息传输完整一致

举个栗子：
假如你在网上下载了一个软件，有300M，然而你不知道你下载的是不是和它的300M一样
这时就需要有个MD5，如果你们两个的MD5值一样，那么说明你下载的300M===它的300M
文件差异越小，MD5的差异越大

### ETag
用cache-Control是不请求，ETage是直接不下载，但还是有请求，但是响应体是空的
打开一个网页，初次打开会有一个ETag，
以后再打开它的时候请求里有一个if-none-match响应头，后面跟的就是MD5
![image.png](https://upload-images.jianshu.io/upload_images/11007474-9217e337d2de516b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



转化为数字 parseInt（a，10） 写法等于 （+1）
