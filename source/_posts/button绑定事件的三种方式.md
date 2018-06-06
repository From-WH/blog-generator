---
title: button绑定事件的三种方式
date: 2018-06-06 21:11:30
tags:
---
##### HTML中为button绑定事件的方式有三种。
---

例如以下标签：

`<button type="submit" id="btn_submit"> submit </button>`

### 使用jquery进行绑定
---
```
$('#btn_submit').click(function(){

});
```

###  使用原生js绑定，
---
注意：Internet Explorer 8 及更早IE版本不支持 addEventListener() 方法，Opera 7.0 及 Opera 更早版本也不支持。 这类浏览器版本要使用 attachEvent() 方法来添加事件
```
document.getElementById("#btn_submit").addEventListener(‘click’, function(){

}, false);
```

补充：addEventListener的第三个参数是用于决定事件模型的，当父元素和子元素都绑定了事件时，这个参数决定先触发哪个事件，false为冒泡事件模型：即子元素绑定的事件先响应，父元素绑定的事件后相应，true问捕获事件模型，与冒泡事件模型执行顺序相反，如：
```
<div id="test_div">
   <button type="button" value ="测试事件顺序" name="测试事件顺序" id="test_button">测试事件顺序</button>
</div> 

document.getElementById('test_div').addEventListener('click', function () {
    console.log('div');
},true)
document.getElementById('test_button').addEventListener('click', function(){
    console.log('test1');
},false);
```

这个例子的事件模型是捕获模型，会先执行div的事件再执行button的事件，这里有个需要注意的地方：决定事件模型的是父元素绑定事件时传的第三个参数，如上例中button绑定事件时传的第三个参数是不起作用的，除非它又包含了子元素。

对事件模型不了解的可以查看改链接：[http://www.cnblogs.com/dtdxrk/archive/2012/06/28/2567132.html](http://www.cnblogs.com/dtdxrk/archive/2012/06/28/2567132.html)

### 直接在button标签中使用onclick绑定
---

`<button type="submit" id="btn_submit" onclick="btnAction()"> submit </button>`

然后在<script>标签中定义btnAtion的方法
```
<script>
        function btnAction()
        { } 

</script>
```

#### 比较：

1、使用jquery绑定，代码简洁，使用方便，事件绑定方式为追加绑定，即绑定多少个方法就执行多少个方法。

在单一绑定的条件下，由于jQuery底层其实也是js实现，所以速度区别并不大。至少“绑定”这个环节并不会成为

速度的瓶颈，除非页面上绑定事件的元素超过上万个，否则响应速度就不必纠结了，只做个事件绑定还是很快的。

所以在做负载等要求不那么严格的“小程序”，从维护的角度上，建议用jQuery绑定，简单清楚，最容易维护。

2、使用原生js与jquery相比的话代码量稍大，但是能让人进一步了解事件绑定的细节，对于熟悉原生js的开发者来说是值得推荐的。

3、使用onclick标签绑定，代码量不大，但是html前端和js前端混在一起，不易于维护。

原则上HTML代码只能体现网页的结构，具体的行为应该使用javascript代码进行绑定。

如果在HTML中用onclick事件混杂js，会导致html前端和js前端的工作混在了一起，难以分离工作任务，

进而难以维护。这种做法临时调试可以，但如果正式成品中不应该出现，

所以不建议使用onclick标签方式进行绑定事件。

