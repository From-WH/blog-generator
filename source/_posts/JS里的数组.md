---
title: JS里的数组
date: 2018-04-09 23:24:41
tags:
---
####Array
Array对象是用来构造数组的全局对象
原型链里有Array.prototype 那他就是一个数组
- Array的不一致性
![image.png](https://upload-images.jianshu.io/upload_images/11007474-1ae9ef0ff335931a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
- 基本类型与复杂类型加NEW与不加的区别
![image.png](https://upload-images.jianshu.io/upload_images/11007474-a340e9c235189781.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
- Array的操作用法
![image.png](https://upload-images.jianshu.io/upload_images/11007474-1b999099464c37cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

![image.png](https://upload-images.jianshu.io/upload_images/11007474-6d2059535970225f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

![image.png](https://upload-images.jianshu.io/upload_images/11007474-aef22d1d0bdcf54b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

![image.png](https://upload-images.jianshu.io/upload_images/11007474-3e2b23ecbe01265b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

- 重点：
数组和对象都是对象，只不过是原型链不同
![image.png](https://upload-images.jianshu.io/upload_images/11007474-d06fc39663f1027b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

####伪数组
伪数组就是在原型链中没有Array.prototype
目前接触到的唯一的伪数组：Argument

####数组的API
- forEach
forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数。

注意: forEach() 对于空数组是不会执行回调函数的
![image.png](https://upload-images.jianshu.io/upload_images/11007474-64c8fa361575a6d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
forEach会遍历['a','b','c']这个数组，对每一项都调用function（value，key）这个函数，调用这个函数会传两个参数

![image.png](https://upload-images.jianshu.io/upload_images/11007474-f698b98765aa2914.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- sort
对数组的元素进行排序，并返回数组。 sort 排序不一定是稳定的默认排序顺序是根据字符串Unicode码点
排序的依据
![image.png](https://upload-images.jianshu.io/upload_images/11007474-d709306f03131d41.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
-join
将一个数组或一个类数组对象的所有元素连接成一个字符串并返回这个字符串。且不会改变数组！
- map
方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。
![image.png](https://upload-images.jianshu.io/upload_images/11007474-a19e1f70d637b2a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
![image.png](https://upload-images.jianshu.io/upload_images/11007474-dab2ff8998682ad1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- filter
方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。 
![image.png](https://upload-images.jianshu.io/upload_images/11007474-4d14117c2e4171bf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- reduce
方法对累加器和数组中的每个元素（从左到右）应用一个函数，将其减少为单个值
![image.png](https://upload-images.jianshu.io/upload_images/11007474-3cc9762ea56e61a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
- reverse() 
将数组中元素的位置颠倒。

第一个数组元素成为最后一个数组元素，最后一个数组元素成为第一个


### PS:箭头函数表达式
最适合用于非方法函数，并且它们不能用作构造函数。

- 基础语法
```
(参数1, 参数2, …, 参数N) => { 函数声明 }
(参数1, 参数2, …, 参数N) => 表达式（单一）
//相当于：(参数1, 参数2, …, 参数N) =>{ return 表达式; }
// 当只有一个参数时，圆括号是可选的：
(单一参数) => {函数声明}
单一参数 => {函数声明}
// 有参数的函数应该写成一对圆括号。
() => {函数声明}
```