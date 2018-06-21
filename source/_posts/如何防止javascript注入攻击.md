---
title: 如何防止javascript注入攻击
date: 2018-06-21 16:56:33
tags:
---
一：什么是html转义？

html转义是将特殊字符或html标签转换为与之对应的字符。如：< 会转义为 &lt;> 或转义为 &gt;像“<script>alert('test');</script>”这段字符会转义为：“&lt;script&gt;alert('test');&lt;/script&gt;”再显示时页面会将&lt;解析为<,&gt;解析为>,从而还原了用户的真实输入,最终显示在页面上 的还是“<script>alert('test');</script>”，即避免了js注入攻击又真实的显示了用户输入。


二：如何转义？
1、通过js实现
```
//转义  元素的innerHTML内容即为转义后的字符  
function htmlEncode ( str ) {  
  var ele = document.createElement('span');  
  ele.appendChild( document.createTextNode( str ) );  
  return ele.innerHTML;  
}  
//解析   
function htmlDecode ( str ) {  
  var ele = document.createElement('span');  
  ele.innerHTML = str;  
  return ele.textContent;  
} 
```

2、通过jquery实现
```
function htmlEncodeJQ ( str ) {  
    return $('<span/>').text( str ).html();  
}  
  
function htmlDecodeJQ ( str ) {  
    return $('<span/>').html( str ).text();  
} 
```
建议使用jquery实现，因为有更好的兼容性


