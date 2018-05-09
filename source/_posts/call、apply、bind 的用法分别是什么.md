---
layout: 
title: call、apply、bind的用法分别是什么
date: 2018-05-09 23:31:13
tags:
---

#### call
call() 方法调用一个函数, 其具有一个指定的this值和分别地提供的参数。
语法：fun.call(thisArg, arg1, arg2, ...)
参数
thisArg
在fun函数运行时指定的this值。需要注意的是，指定的this值并不一定是该函数执行时真正的this值，如果这个函数处于非严格模式下，则指定为null和undefined的this值会自动指向全局对象(浏览器中就是window对象)，同时值为原始值(数字，字符串，布尔值)的this会指向该原始值的自动包装对象。
arg1, arg2, ...
指定的参数列表。
---
#### apply
apply() 方法调用一个函数, 其具有一个指定的this值，以及作为一个数组（或类似数组的对象）提供的参数。
apply 的作用和 call 一样，只是在调用的时候，传参数的方式不同。区别是 apply 接受的是数组参数，call 接受的是连续参数。
语法：func.apply(thisArg, [argsArray])
参数：
thisArg
可选的。在 func 函数运行时使用的 this 值。需要注意的是，使用的 this 值并不一定是该函数执行时真正的 this 值，如果这个函数处于非严格模式下，则指定为 null 或 undefined 时会自动替换为指向全局对象（浏览器中就是window对象），同时值为原始值（数字，字符串，布尔值）的 this 会指向该原始值的包装对象。
argsArray
可选的。一个数组或者类数组对象，其中的数组元素将作为单独的参数传给 func 函数。如果该参数的值为null 或 undefined，则表示不需要传入任何参数。从ECMAScript 5 开始可以使用类数组对象。浏览器兼容性请参阅本文底部内容。
---
#### bind
语法：fun.bind(thisArg[, arg1[, arg2[, ...]]])
bind()方法创建一个新的函数, 当被调用时，将其this关键字设置为提供的值，在调用新函数时，在任何提供之前提供一个给定的参数序列。
bind 接受的参数跟 call 一致，只是 bind 不会立即调用，它会生成一个新的函数，你想什么时候调就什么时候调
参数
thisArg
当绑定函数被调用时，该参数会作为原函数运行时的 this 指向。当使用new 操作符调用绑定函数时，该参数无效。
arg1, arg2, ...
当绑定函数被调用时，这些参数将置于实参之前传递给被绑定的方法。


