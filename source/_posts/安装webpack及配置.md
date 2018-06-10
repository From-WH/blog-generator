---
title: 安装webpack及配置
date: 2018-06-10 22:58:49
tags:工具
---

### 首先卸载你之前配置失败的webpack
---

卸载webpack：
npm uninstall webpack -g

### 安装webpack
---
- 准备工作
在桌面创建一个文件夹
`mkdir webpack-demo`
然后`cd webpcak-demo`
- 安装webpack
全局安装：`sudo npm i -g webpack@3.6.0`
查看是否安装成功：`webpack --help`
看到如下图说明成功：
![image.png](https://upload-images.jianshu.io/upload_images/11007474-21da5032ac3460b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/740)
接下来命令行输入：`npm init`
出现的填空全部点回车就好
### 创建文件
创建下面四个文件（划掉的不用创建）
![image.png](https://upload-images.jianshu.io/upload_images/11007474-c9a91068e6875688.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
内容分别是：
SRC / index.js：
```
import bar from './bar';

bar();
```
SRC / bar.js：
```
export default function bar() {
  //
}
```
webpack.config.js：
```
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
      path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js'
  }
};
```
page.html：
```
<!doctype html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
    <script src="dist/bundle.js"></script>
  </body>
</html>
```
然后命令行输入`webpack`如出现如下图
![image.png](https://upload-images.jianshu.io/upload_images/11007474-529a5938967fbf49.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
然后去你的文件夹看，出现了一个built的文件夹里面还有一个js文件
然后给你的webpack.config.js文件加如下代码
```
module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /(node_modules|bower_components)/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['env']
          }
        }
      }
    ]
  }
```
这里很多人加错，应该成为如下：
```
const path = require('path')

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /(node_modules|bower_components)/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['env']
          }
        }
      }
    ]
  }
}
```
好了继续在命令行输入`webpack`
发现又特么错，是不是慌得一批，不要急，看报错
![image.png](https://upload-images.jianshu.io/upload_images/11007474-018f7d5c585c8fa9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/740)
他不说没有`babel-loader`嘛，按上不就好了嘛
继续命令行输入：`npm i babel-loader`
完成后继续输入`webpack`
又错！
![image.png](https://upload-images.jianshu.io/upload_images/11007474-e0c0cda16a5196fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/740)
不废话了，继续安装：`npm i babel-core`
在运行`webpack`，
![image.png](https://upload-images.jianshu.io/upload_images/11007474-5e564457b2c5b8d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/740)

又特么错！是不是要疯了？

心中mmp的继续安装吧
他说我们没有env
运行’npm i babel-preset-env‘
再运行`wenpack`

WCO！终于不报错了

打开文件夹中的page.html，发现毛都没有

来改一下 bar.js 吧：
```
export default function bar() {
  alert('Hello Webpack!')
}
```
在运行`webpack`
点开文件，发现页面出现了Hello Webpack！

我们把js模块化
在src文件里创建js文件
在里面添加model1.js、model2.js（这两个是你要用的模块）
先要定义一下模块1和模块2
```
function fn() {
    console.log(2)
}
export default fn  //如果有人引用我 我就把fn传给他
```
1、2的内容可以一样
还有一个入口app.js
```
import x from './module-1'       /得到一个文件从module1 x就是默认导出的那个fn（module里的那个）
import y from './module-2'
import '../css/main.scss'

x()
console.log('傻逼webpack')
y()
```

这时候运行webpack就可以看到在dist里面的bundle.js里有我们下的两个模块的js文件

在src文件里创建js文件
在里面添加model1.js、model2.js（这两个是你要用的模块）
先要定义一下模块1和模块2
```
function fn() {
    console.log(2)
}
export default fn  //如果有人引用我 我就把fn传给他
```
1、2的内容可以一样
还有一个入口app.js
```
import x from './module-1'       /得到一个文件从module1 x就是默认导出的那个fn（module里的那个）
import y from './module-2'
import '../css/main.scss'

x()
console.log('傻逼webpack')
y()
```
这时候运行webpack就可以看到在dist里面的bundle.js里有我们下的两个模块的js文件

### 接下来我们把css也转化一下吧
---
你需要配置一下内容
```
    css-loader
    sass-loader
    style-loader
    node-sass
```
然后在webpack.config.js里的rules后面加上
```
            {
                test: /\.scss$/,     //获取要输出的文件格式
                use: [{
                    loader: "style-loader"      //第三部 把刚才的common js字符串转为style
                }, {
                    loader: "css-loader"       //第二部，把css转为common js字符串
                }, {
                    loader: "sass-loader",     //获取后第一步 把sass转为css
                    options: {
                        includePaths: ["absolute/path/a", "absolute/path/b"]
                    }
                }]
            }
```

说明已经基本的配置完成！
是不是真的很难用啊～
%>_<%～





