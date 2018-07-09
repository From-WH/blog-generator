---
title: 前端面试必考篇—JS/DOM
date: 2018-07-09 20:34:30
tags:
---
### JS

1.  JS 有哪些数据类型？ string number boolean undefined null object symbol object 包括了数组、函数、正则、日期等对象 一旦出现（数组、函数、正则、日期、NaN）直接0分

2.  （必考） Promise 怎么使用？

    *   then

        ```
        $.ajax(...).then(成功函数, 失败函数)

        ```

    *   链式 then

        ```
        $.ajax(...).then(成功函数, 失败函数).then(成功函数2, 失败函数2)

        ```

    *   如何自己生成 Promise 对象

        ```
        function xxx(){
            return new Promise(function(resolve, reject){
                setTimeout(()=>{
                    resolve() 或者 reject()
                },3000)
            })
        }
        xxx().then(...)

        ```

3.  （必考） AJAX 手写一下？

    ```
    let xhr = new XMLHttpRequest()
    xhr.open('POST', '/xxxx')
    xhr.onreadystatechange = function(){
        if(xhr.readyState === 4 && xhr.status === 200){
            console.log(xhr.responseText)
        }
    }
    xhr.send('a=1&b=2')

    ```

4.  （必考）闭包是什么？

    ```
    function (){
        var n = 0
        return function(){
            n += 1
        }
    }

    let  adder = ()
    adder() // n === 1
    adder() // n === 2
    console.log(n) // n is not defined

    ```

    正确参考：[https://zhuanlan.zhihu.com/p/2248690810](https://zhuanlan.zhihu.com/p/22486908)

5.  （必考）这段代码里的 this 是什么？

    1.  fn() 里面的 this 就是 window
    2.  fn() 是 strict mode，this 就是 undefined
    3.  a.b.c.fn() 里面的 this 就是 a.b.c
    4.  new F() 里面的 this 就是新生成的实例
    5.  () => console.log(this) 里面 this 跟外面的 this 的值一模一样 正确参考：[https://zhuanlan.zhihu.com/p/238042474](https://zhuanlan.zhihu.com/p/23804247)
6.  （必考）什么是立即执行函数？使用立即执行函数的目的是什么？

    ```
    ;(function (){
        var name
    }())
    ;(function (){
        var name
    })()
    !!!!!!!function (){
        var name
    }()
    ~function (){
        var name
    }()

    ```

    造出一个函数作用域，防止污染全局变量

    ES 6 新语法 { let name }

7.  async/await 语法了解吗？目的是什么？

    ```source-js
    function returnPromise(){
        return new Promise( function(resolve, reject){
            setTimeout(()=>{
                resolve('fuck')
            },3000)
        })
    }

    returnPromise().then((result)=>{
        result === 'fuck'
    })

    var result = await returnPromise()
    result === 'fuck'
    ```

    把异步代码写成同步代码。

8.  如何实现深拷贝？

    1.  JSON 来深拷贝

    ```
       var a = {...}
       var b = JSON.parse( JSON.stringify(a) )

    ```

    缺点：JSON 不支持函数、引用、undefined、RegExp、Date……

    2.  递归拷贝

        ```
        function clone(object){
            var object2
            if(! (object instanceof Object) ){
                return object
            }else if(object instanceof Array){
                object2 = []
            }else if(object instanceof Function){
                object2 = eval(object.toString())
            }else if(object instanceof Object){
                object2 = {}
            }
            for(let key in object){
                object2[key] = clone(object[key])
            }
            return object2
        }

        ```

    3.  环

    4.  RegExp、Date、Set、Symbol、WeakMap

9.  如何实现数组去重？

    1.  计数排序的逻辑（只能正整数）

        ```
        var a = [4,2,5,6,3,4,5]
        var hashTab = {}
        for(let i=0; i<a.length;i++){
            if(a[i] in hashTab){
                // 什么也不做
            }else{
                hashTab[ a[i] ] = true
            }
        }
        //hashTab: {4: true, 2: true, 5: true, 6:true, 3: true}
        console.log(Object.keys(hashTab)) // ['4','2','5','6','3']

        ```

    2.  Set 去重

        ```
        Array.from(new Set(a))

        ```

    3.  WeakMap 任意类型去重

10.  如何用正则实现 string.trim() ？

```
function trim(string){
    return string.replace(/^\s+|\s+$/, '')
}

```

11.  JS 原型是什么？

    *   举例
        1.  var a = [1,2,3]

        2.  只有0、1、2、length 4 个key

        3.  为什么可以 a.push(4) ，push 是哪来的？

        4.  a.**proto** === Array.prototype

        5.  push 就是沿着 a.**proto** 找到的，也就是 Array.prototype.push

        6.  Array.prototype 还有很多方法，如 join、pop、slice、splice

        7.  Array.prototype 就是 a 的原型（**proto**）

            参考：[https://zhuanlan.zhihu.com/p/230900412](https://zhuanlan.zhihu.com/p/23090041)

12.  ES 6 中的 class 了解吗？

    *   把 MDN class 章节看完
    *   记住一个例子
13.  JS 如何实现继承？

    *   原型链

        ```source-js
        function Animal(){
            this.body = '肉体'
        }
        Animal.prototype.move = function(){

        }

        function Human(name){
            Animal.apply(this, arguments)
            this.name = name
        }
        // Human.prototype.__proto__ = Animal.prototype // 非法

        var f = function(){}
        f.prototype = Animal.prototype
        Human.prototype = new f()

        Human.prototype.useTools = function(){}

        var frank = new Human()
        ```

    *   extends 关键字

        ```
        class Animal{
            constructor(){
                this.body = '肉体'
            },
            move(){}
        }
        class Human extends Animal{
            constructor(name){
                super()
                this.name = name
            },
            useTools(){}
        }
        var frank = new Human()

        ```

14.  相关题目直接反着答（放弃）

### DOM

1.  DOM 事件模型是什么？

    1.  冒泡
    2.  捕获
    3.  [如果这个元素是被点击的元素，那么捕获不一定在冒泡之前，顺序是由监听顺序决定的10](http://jsbin.com/raqakog/1/edit?js,console,output)。
2.  移动端的触摸事件了解吗？

    1.  touchstart touchmove touchend touchcancel
    2.  模拟 swipe 事件：记录两次 touchmove 的位置差，如果后一次在前一次的右边，说明向右滑了。
3.  事件委托是什么？有什么好处？

    1.  假设父元素有4个儿子，我不监听4个儿子，而是监听父元素，看触发事件的元素是哪个儿子，这就是事件委托。
    2.  可以监听还没有出生的儿子（动态生成的元素）。省监听器。

    ```
    function listen(element, eventType, selector, fn){
        element.addEventListener(eventType, e=>{
            if(e.target.matches(selector)){
                fn.call(el, e, el)
            }
        })
    }// 有 bug 但是可以应付面试官的事件委托

    ```

    ```
    function listen(element, eventType, selector, fn) {
        element.addEventListener(eventType, e => {
            let el = e.target
            while (!el.matches(selector)) {
                if (element === el) {
                    el = null
                    break
                }
                el = el.parentNode
            }
            el && fn.call(el, e, el)
        })
        return element
    } // 工资 12k+ 的前端写的事件委托
    listen(ul, 'click', 'li', ()=>{})

    ul>li*5>span

    ```

