---
title: 关于Hexo博客搭建的教程
date: 2018-03-18 19:52:46
tags: hexo博客
---
### 开始创建
1.进入一个安全的目录，比如 `cd ~/Desktop` 或者 `cd ~/Documents`
2.`npm install -g hexo-cli`，安装 Hexo
3.`hexo init myBlog`
4.`cd myBlog`
5.`npm i`
6.`hexo new 开博大吉`，你会看到一个 md 文件的路径
7.`start xxxxxx.md`（XXX此时为开博大吉）
8.`start _config.yml`，编辑网站配置
9._config.yml内要编辑的内容
- 把第 6 行的 `title:xxx`  改成你想要的博客名字
- 把第 9 行的 `author:xxx` 改成姓名
- 把最后一行的 `type` 改成 `type: git`（记住前面有个空格）
- 在最后一行后面新增一行，左边与 `type` 平齐，加上一行 `repo: 仓库地址：xxxxx`（在github上创建一个空的仓库，此处填写地址，最好为SSH地址）
10.`npm install hexo-deployer-git --save`，安装 git 部署插件
11.`hexo deploy`
12.进入「你的用户名.github.io」对应的 repo，打开 GitHub Pages 功能，如果已经打开了，就直接点击预览链接
13.搞定！
### 第二篇博客
1.`hexo new 第二篇博客`
2.复制显示的路径，使用 start 路径 来编辑它
3.`hexo generate`
4.`hexo deploy`
5.去看你的博客，应该能看到第二篇博客了
### 换主题
https://github.com/hexojs/hexo/wiki/Themes 上面有很多主题随意挑选，按下面步骤更换
1.随便找一个主题，进入主题的 GitHub 首页，比如我找的是 https://github.com/iissnan/hexo-theme-next
2.复制它的 SSH 地址或 HTTPS 地址，假设地址为 git@github.com:iissnan/hexo-theme-next.git
3.`cd themes`
4.`git clone git@github.com:iissnan/hexo-theme-next.git`
5.`cd ..`
6.将 _config.yml 的第 75 行改为 `theme: hexo-theme-next`，保存
7.`hexo generate`
8.`hexo deploy`
9.等一分钟，然后刷新你的博客页面，你会看到一个新的外观。如果不喜欢这个主题，就回到第 1 步，重选一个主题
10.之后的主题切换直接在`_config.yml` 的第 75 行进行修改名字即可（前提主题以及下载到themes中）
## 切记：仓库（你的用户名.github.io）名要与GitHub用户名一致！切记！否则你将永远看不到主题！！！
## 切记：仓库（你的用户名.github.io）名要与GitHub用户名一致！切记！否则你将永远看不到主题！！！
## 切记：仓库（你的用户名.github.io）名要与GitHub用户名一致！切记！否则你将永远看不到主题！！！