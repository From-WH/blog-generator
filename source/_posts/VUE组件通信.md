---
title: VUE组件通信
date: 2018-07-06 19:48:57
tags:
---
# 父子通信

html
```
<script src="https://unpkg.com/vue"></script>

<div id="app">
  <p>{{ message }}</p>
  <button @click="ccc = true">打开</button>
  <child v-show='ccc' @close="ccc=false"></child>
</div>

```
js
```
Vue.component('child',{
template:`
<div>我是儿子<button @click="$emit('close')">关闭</button></div>
`
})
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!',
    ccc:false
  }
})
```
儿子没有办法自己关闭自己，需要告诉父亲，由父亲进行关闭。

# 兄弟通信
查看CSDN[博客](https://blog.csdn.net/u013034014/article/details/54574989?locationNum=2&fps=1)
[博客2](https://www.w3ctrain.com/2016/08/02/text-overflow-mutiple-line/)
# 爷孙通信
vue的爷孙通信特别麻烦，所以有了vuex。

孙子没有冒泡
不存在的，只能父子通信，如果你想爷孙通信，就传递事件吧，一层一层的传上来。
```
<script src="https://unpkg.com/vue"></script>

<div id="app">
  <p>{{ message }}</p>
  <button @click="ccc = true">打开</button>
  <child :visiable="ccc" @close="ccc=false"></child>
</div>
```
```
Vue.component('child',{
  props:['visiable'],
template:`
<div v-show="visiable" @click="$emit('close')">我是老二<sunzi></div>

`
})
Vue.component('sunzi',{
  template:`
<div>我是老三<button @click="$emit('close')">关闭</button></div>
`
})
new Vue({
  el: '#app',
  data: {
    message: '我是老大',
    ccc:false
  }
})
```

