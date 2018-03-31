---
title: HTML常用标签
date: 2018-03-20 22:21:16
tags:
---
# HTML（HypeText Markup language）超文本标记语言
- 版本历史：
HTML 的版本（W3C 组织制定规范）
1.HTML 4.01
2.XHTML
3.HTML 5（与H5没关系，可以运行在微信上的网页就叫H5）
4.HTML 5.1（已经发布）
[HTML specifications标准文档](https://www.w3.org/TR/html52/)由W3C组织编写
- DOCTYPE
用来选择文档类型
html / head / body
省略标签
常见标签：**a、form、input、button、h1、p、ul、ol、small、strong、div、span、kbd、video、audio、svg**
基本上，你知道标签对应单词的意思，就知道这个标签怎么用了（语义化）
除了 div 和 span，其他标签都有默认样式
html标签
如果开始不是一个注释，开头标签可以省略
如果结尾不是一个注释，那么结尾标签也可以省略
- head标签
根据协议规定，在没有内容的情况下是可以省略的
- body标签
只要第一个不是空格且没有注释的情况下也是可以不写的
```
**<a> anchor 锚点
<form> 表单
<input> 输入
<buttom> 点击
<h1>主标题
<p>paragraph段落
<ul>unordered list 没有顺序的列表
<ol>ordered list 有顺序的列表
<dl>description list 描述列表
<dt>description term 描述词语
<dd>定义
<small>不重要的字
<strong> 重要的字（有情感，逻辑）<bold>（物理状态）
<div>divide 划分（没有任何意义的标签class）
<span> 横向的划分（没有任何意义的标签，需要搭配class）
<kbd> keyboard键盘
<video> 视频
<audio> 音频
<svg> Scalable Vector Graphics不规则的图形
<alt> alternative可选内容**
```
除了 div 和 span，其他标签都有默认样式
- a标签
download属性：表示是用来下载
跳转页面发起的是GET（获取）请求
- form
跳转页面一般发起的是POST（上传）请求
如果form表单里面没有【提交按钮】就无法提交这个form
```
<form action="user" method="POST">  
<input type="text" name="username">  
<input type="password" name="password">  
<input type="submit" value="提交">  
</form>
```
## type
- button
`<button>button</button>`如果没有type默认升级为subline
`<button type="button">button</button>`没有提交作用
- checkbox
![image.png](https://upload-images.jianshu.io/upload_images/11007474-ddd398b6c254b935.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
设置label for与input的ID进行关联，此时点击文字就能勾选
老司机是这样写的用`label`将`input`包起来就可以达到和上面同样的效果
![image.png](https://upload-images.jianshu.io/upload_images/11007474-eb9e1cf2d70be7a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
- radio 单选
只能选择一个，前提是name要设定一致
- -select 下拉列表
![image.png](https://upload-images.jianshu.io/upload_images/11007474-a82d1f2aa92fc681.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
disable不可以选择，selecated默认选择
value是空  则没有值
select中如果添加一个multiple则可以多选
![image.png](https://upload-images.jianshu.io/upload_images/11007474-c15373207d9f5b50.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- textarea 文本域
一定要给一个name否则无法提交
resize：none设置不可以被拉伸，用CSS设置宽高
## table 表格
- th（table row）表示表头  td（table data）表示信息
colgroup中col设置每一列宽高
![image.png](https://upload-images.jianshu.io/upload_images/11007474-c0bbdae019586e73.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- <thead><tbody><tfoot>的顺序不影响呈现出的内容
CSS中加入`border-collapse：collapse；`可以使表格直接的空隙取消
![image.png](https://upload-images.jianshu.io/upload_images/11007474-57bc84d14d1b7e14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
        <table>    
            <thead>
                <tr>
                    <th>姓名</th><th>学校</th><th>年级</th><th>班级</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th>小红</th><td>育红小学</td><td>三年级</td><td>七班</td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <th>小明</th><td>育红小学</td><td>三年级</td><td>八班</td>
                </tr>
            </tfoot>
        </table>
```
![image.png](https://upload-images.jianshu.io/upload_images/11007474-ba2822a140b1cbf8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
