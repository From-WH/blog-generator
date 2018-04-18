---
title: jQuery
date: 2018-04-15 18:43:19
tags: jQuery
---
#### 1.封装
函数封装是一种函数的功能，它把一个程序员写的一个或者多个功能通过函数、类的方式封装起来，对外只提供一个简单的函数接口。
```
let classes = { 'a': true, 'b': false, 'c': true }
      for (let key in classes) {
       let value = classes[key]
            if (value) {
               tim4.classList.add(key)
            } else {
               tim4.classList.remove(key)
               }
      }   
```
封装后：
```
        function addClass(node,classes) {
            for (let key in classes) {
                let value = classes[key]
                if (value) {
                    node.classList.add(key)
                } else {
                    node.classList.remove(key)
                }
            }
        }
        直接addClass（）就可以了
```
代码优化守则：
凡是看起来相似的代码就存在优化的可能

obj.x()
ogj.['x']()
上面两个相等

#### 2.命名空间
```
        window.wwNode = {}   //命名空间
        wwNode.xxx = xxx
        wwNode.addClass = addClass

        wwNode.xxx(tim4)
```

#### 3.this
this是call的第一个参数

####4.jQuery
jQuery接受一个旧的节点，返回一个新的对象，这个对象就是jquery的对象
instanceof 运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性。

#### 5.链式操作
       .  .  . 懂了吧

####6.jQuery的简单实用
jQuery 是一个 JavaScript 库
jQuery接受一个旧的节点，返回一个新的对象，新的对象有新的API，这个对象就是jQuery的对象
window.$ = jQuery
用全局变量$就相当于在用jQury
习俗：如果这个对象是$（jQuery）的就在对象前面加一个$，说明这是jQuery构造的，可以用jQuery的API

```
function getSibilings(node) {  //自己设计的API，getSibilings
    var allChildren = node.parentNode.children  //获取这个元素的所有兄弟姐妹
    var array = { length: 0 }                    
    for (let i = 0; i < allChildren.length; i++) {      
        if (allChildren[i] !== node) {                
            array[array.length] = allChildren[i]
            array.length += 1                   
        }
    }
    return array
}
```
```
新的接口 BetterNode 
window.jQuery = function (node) {
       return {
            allsiblings: function () {
               var allChildren = node.parentNode.children  //获取这个元素的所有兄弟姐妹
               var array = { length: 0 }
            for (let i = 0; i < allChildren.length; i++) {
                  if (allChildren[i] !== node) {
                        array[array.length] = allChildren[i]
                         array.length += 1
                  }
             }
         return array
         },
         allClass: function (classes) {       
              for (let key in classes) {                   //遍历这个classes
                    let value = classes[key]               //将classes的【key】给value
                    let madeClass = value ? 'add' : 'remove'
                     node.classList[madeClass](key)
                    }
               }
          }
 }
var Node2 = jQuery(tim3)  //jQuery接受一个旧的节点，返回一个新的对象，新的对象由新的API，这个对象就是jQuery的对象
Node2.allsiblings()
Node2.allClass()
```
```
确定是节点还是字符串
window.jQuery = function (nodeOrSelector) {
    let nodes
    if (nodeOrSelector === 'string') {
        let temp = document.querySelector(nodeOrSelector)
        for( let i=0; i< temp.length;i++ ){
            nodes[i] = temp[i]
            node.length = temp.length
        }else if(nodeOrSelector instanceof Node){
            nodes = {
                0 : nodeOrSelector,
                length :1
            }
        }
    }
}
```
实现一个 jQuery 的 API
```
window.jQuery = function (nodeOrSelector) {     获取节点或字符串
    let $nodes = {}                             //初始化一个空对象，将之后字符串或数组放进去
    if (typeof nodeOrSelector === 'string') {   //识别输入的是节点还是字符串
        let temp = document.querySelectorAll(nodeOrSelector)
        for (let i = 0; i < temp.length; i++) {
            $nodes[i] = temp[i]
        }
        $nodes.length = temp.length
    } else if (nodeOrSelector instanceof Node) {     //如果是节点那么久把它放入伪数组
        nodes = {
            0: nodeOrSelector,
            length: 1
        }
    }
    $nodes.addClass = function (classes) {      //获取参数，遍历找到相关节点，给相关节点添加value
        classes.forEach((value) => {
            for (let i = 0; i < $nodes.length; i++) {
                $nodes[i].classList.add(value)
            }
        })
    }
    $nodes.setText = function (text) {
        if (text === undefined) {               //如果文本为空，则添加文本
            var texts = []
            for (let i = 0; i < $nodes.length; i++) {
                texts.push($nodes[i].textContent)
            }
            return texts
        } else {                      //否则输出文本内容
            for (let i = 0; i < $nodes.length; i++) {
                $nodes[i].textContent = text
            }
        }
    }
    return $nodes
}
window.$ = jQuery
var $div = $('div')
$div.addClass(['red']) // 可将所有 div 的 class 添加一个 red
$div.setText('hi') // 可将所有 div 的 textContent 变为 hi
```

#### 7.jQuery与DOM转换
jQuery对象和DOM对象的转换
>jquery转dom
>var div = $div[0]  //这样jquery就转换成了DOM对象，或div = $div.get(0)

>dom转jquery
>var $div = $(div);  //这样dom对象div，就转换成了jquery对象

#### 8.[jQueryAPI方法的中文网站](http://cndevdocs.com/)
