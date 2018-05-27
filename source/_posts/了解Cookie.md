---
title: 了解Cookie
date: 2018-05-27 23:07:27
tags:
---

**前端永远不要读/写Cookie**

### 登录、注册
- 注册页面js代码：
```
  <script>
    let $form = $('#signUpForm')
    $form.on('submit', (e)=>{
      e.preventDefault()
      let hash = {}
      let need = ['email', 'password', 'password_confirmation'] //查找到name为email、password的元素
      need.forEach((name)=>{ 
        let value = $form.find(`[name=${name}]`).val() //获取用户输入的值
        hash[name] = value           //然后把这个值放到这个hsah里，就是email等于用户输入的email的值
      })
      $form.find('.error').each((index, span)=>{    //初始是找到所有的.error把他们设为空
        $(span).text('')
      })
      if(hash['email'] === ''){            //验证这个hash
        $form.find('[name="email"]').siblings('.error')
          .text('填邮箱呀同学')
        return
      }
      if(hash['password'] === ''){
        $form.find('[name="password"]').siblings('.error')
          .text('填密码呀同学')
        return
      }
      if(hash['password_confirmation'] === ''){
        $form.find('[name="password_confirmation"]').siblings('.error')
          .text('确认密码呀同学')
        return
      }
      if(hash['password'] !== hash['password_confirmation']){
        $form.find('[name="password_confirmation"]').siblings('.error')
          .text('密码不匹配')
        return
      }
      $.post('/sign_up', hash)   //用ajax 路径是sign_up  内容是hash
        .then((response)=>{     //用到了promise 成功了打这个
          console.log(response)
        }, (request)=>{     //失败了打这个
          let {errors} = request.responseJSON
          if(errors.email && errors.email === 'invalid'){ //如果这个email存在而且这个email等于invalid
            $form.find('[name="email"]').siblings('.error')  
              .text('邮箱格式错误')
          }
        })
    })
  </script>
```
注册页面Node.js代码
```
else if(path === '/sign_up' && method === 'GET'){   //路径为。。。方法为。。。
    let string = fs.readFileSync('./sign_up.html', 'utf8')  //读取一下当前目录下的sign_up.html文件 以utf8的编码读取
    response.statusCode = 200   //响应的状态码为200
    response.setHeader('Content-Type', 'text/html;charset=utf-8')  //content-type 是。。。。
    response.write(string)           // 然后把字符串放在第四部分
    response.end()                   //结束
  }else if(path === '/sign_up' && method === 'POST'){    
    readBody(request).then((body)=>{   //promise  读取请求的第四部分
      let strings = body.split('&') // ['email=1', 'password=2', 'password_confirmation=3'] 
      let hash = {} 
      strings.forEach((string)=>{
        // string == 'email=1'
        let parts = string.split('=') //  将字符串由=为中间隔开，变为['email', '1'] 
        let key = parts[0]      
        let value = parts[1]
        hash[key] = decodeURIComponent(value) // hash['email'] = '1' 
      })
      let {email, password, password_confirmation} = hash //解构赋值
      if(email.indexOf('@') === -1){       //找email里面有没有@符号 indexOF是吧%40转换为@
        response.statusCode = 400
        response.setHeader('Content-Type', 'application/json;charset=utf-8') //后端传json
        response.write(`{                          
          "errors": {
            "email": "invalid"
          }
        }`)
      }else if(password !== password_confirmation){
        response.statusCode = 400
        response.write('password not match')
      }else{
        var users = fs.readFileSync('./db/users', 'utf8')
        try{
          users = JSON.parse(users) // []  接受一个字符返回一个对象
        }catch(exception){
          users = []
        }
        let inUse = false
        for(let i=0; i<users.length; i++){
          let user = users[i]
          if(user.email === email){
            inUse = true
            break;
          }
        }
        if(inUse){
          response.statusCode = 400
          response.write('email in use')
        }else{
          users.push({email: email, password: password})
          var usersString = JSON.stringify(users)
          fs.writeFileSync('./db/users', usersString)
          response.statusCode = 200
        }
      }
      response.end()
    })
  }
```
注册成功后就跳转登录页面
- 登录页面js代码
```
  <script>
    let $form = $('#signInForm')
    $form.on('submit', (e)=>{
      e.preventDefault()
      let hash = {}
      let need = ['email', 'password']
      need.forEach((name)=>{
        let value = $form.find(`[name=${name}]`).val()
        hash[name] = value
      })
      $form.find('.error').each((index, span)=>{
        $(span).text('')
      })
      if(hash['email'] === ''){
        $form.find('[name="email"]').siblings('.error')
          .text('填邮箱呀同学')
        return
      }
      if(hash['password'] === ''){
        $form.find('[name="password"]').siblings('.error')
          .text('填密码呀同学')
        return
      }
      $.post('/sign_in', hash)  
        .then((response)=>{
          window.location.href = '/'  //如果登录成功就跳转至主页
        }, (request)=>{
          alert('邮箱与密码不匹配')
        })
    })
  </script>
```
登录页面Node.js代码
```
else if(path==='/sign_in' && method === 'GET'){
    let string = fs.readFileSync('./sign_in.html', 'utf8')
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/html;charset=utf-8')
    response.write(string)
    response.end()
  }else if(path==='/sign_in' && method === 'POST'){
    readBody(request).then((body)=>{
      let strings = body.split('&') // ['email=1', 'password=2', 'password_confirmation=3']
      let hash = {}
      strings.forEach((string)=>{
        // string == 'email=1'
        let parts = string.split('=') // ['email', '1']
        let key = parts[0]
        let value = parts[1]
        hash[key] = decodeURIComponent(value) // hash['email'] = '1'
      })
      let {email, password} = hash
      var users = fs.readFileSync('./db/users', 'utf8')
      try{
        users = JSON.parse(users) // []
      }catch(exception){
        users = []
      }
      let found
      for(let i=0;i<users.length; i++){
        if(users[i].email === email && users[i].password === password){
          found = true
          break
        }
      }
      if(found){
        response.setHeader('Set-Cookie', `sign_in_email=${email}`)
        response.statusCode = 200
      }else{
        response.statusCode = 401
      }
      response.end()
    })
  }
```

### 判断用户是否已经注册
```
      else{
        var users = fs.readFileSync('./db/users', 'utf8')
        try{
          users = JSON.parse(users) // []  接受一个字符返回一个对象
        }catch(exception){
          users = []
        }
        let inUse = false     
        for(let i=0; i<users.length; i++){   遍历这个users
          let user = users[i]      user等于第i个
          if(user.email === email){
            inUse = true       //说明已经注册
            break;
          }
        }
        if(inUse){              //如果inUse存在说明已经注册
          response.statusCode = 400
          response.write('email in use')
        }else{                    //否则就把这个用户的email 密码等信息存入users这个文件里
          users.push({email: email, password: password})
          var usersString = JSON.stringify(users) 
          fs.writeFileSync('./db/users', usersString)
          response.statusCode = 200
        }
      }
```
### Cookie
上面代码完成时（其实已经加入了Cookie，我懒得删了）发现不管等不登录都可以进入主页，那用户干嘛还要注册呢
所以这时候就需要cookie了，给每个注册过的人一个身份：
```
# if(found){
#        response.setHeader('Set-Cookie', `sign_in_email=${email}`) //这句代码给用户加上了一个标记
#        response.statusCode = 200
# }
```
如果给后面加上HttpOnlyjs就无法随意修改Cookie了，但是用户还是可以修改
```
# response.setHeader('Set-Cookie', `sign_in_email=${email}；HttpOnly`)
```

#### 设置cookie过期时间
1.  cookie的expires属性和max-age属性
*   ### expires属性

    指定了coolie的生存期，默认情况下coolie是暂时存在的，他们存储的值只在浏览器会话期间存在，当用户推出浏览器后这些值也会丢失，如果想让cookie存在一段时间，就要为expires属性设置为未来的一个过期日期。现在已经被max-age属性所取代，max-age用秒来设置cookie的生存期。

*   ### path属性

    它指定与cookie关联在一起的网页。在默认的情况下cookie会与创建它的网页，该网页处于同一目录下的网页以及与这个网页所在目录下的子目录下的网页关联。

*   ### domain属性

    domain属性可以使多个web服务器共享cookie。domain属性的默认值是创建cookie的网页所在服务器的主机名。不能将一个cookie的域设置成服务器所在的域之外的域。
    例如让位于order.example.com的服务器能够读取catalog.example.com设置的cookie值。如果catalog.example.com的页面创建的cookie把自己的path属性设置为“/”，把domain属性设置成“.example.com”，那么所有位于catalog.example.com的网页和所有位于orlders.example.com的网页，以及位于example.com域的其他服务器上的网页都可以访问这个coolie。

*   ### secure属性

    它是一个布尔值，指定在网络上如何传输cookie，默认是不安全的，通过一个普通的http连接传输

2.过时了的expires
```
Set-Cookie: name=Nicholas; expires=Sat, 02 May 2009 23:38:25 GMT
//星期六 5月2号 2009年 23:38:25时过期
```
![image.png](https://upload-images.jianshu.io/upload_images/11007474-f2d8d94e212c0976.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 什么是路由

原理和路由器原理相同，我就简单概述下：不同的请求地址会交给路由处理来转发给相应的控制器处理，所以说路由就可以在转发前修改转发地址，你可以在这上面大作文章。为什么要使用路由？      传统web开发是每一个请求地址都会请求服务器来进行处理，但是用户有些操作则无需请求服务器，直接页面端修改下逻辑就能达到目的，这种最好使用路由，也许题主会有疑问：直接使用js处理下不就行了。使用js直接处理这些是可以的，事实上以前我们也这么做，但是这样做不便于用户收藏当前页，因为使用js时并不更新url，但是使用路由时，url也是随着改变的，用户浏览到一个网页时可以直接复制或收藏当前页的url给别人，这种方式对于搜索引擎和用户来说都是友好的。
以下就是一个sign_up的路由
`else if(){}`就是路由
```
else if(path === '/sign_up' && method === 'GET'){ 
    let string = fs.readFileSync('./sign_up.html', 'utf8')  //读取一下当前目录下的sign_up.html文件 以utf8的编码读取
    response.statusCode = 200   //响应的状态码为200
    response.setHeader('Content-Type', 'text/html;charset=utf-8')  //content-type 是。。。。
    response.write(string)           // 然后把字符串放在第四部分
    response.end()                   //结束
  }
```


- indexOf()
indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置。
语法
stringObject.indexOf(searchvalue,fromindex)
searchvalue	必需。规定需检索的字符串值。
fromindex	可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。
如果要检索的字符串值没有出现，则该方法返回 -1。

URL在李爵士发明的时候，@在服务器里只显示%40，所以需要翻译一下，`decodeURIcomponent()`
- JSON.stringify()
把一个对象转化为字符串

- try{}catch(){}
```
try{
           users = JSON.parse(users) // []  接受一个字符返回一个对象
        }catch(exception){       //如果上面不符合就用下面这句
          users = []
        }
```




