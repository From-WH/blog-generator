---
title: Git+GitHub的使用
date: 2018-03-20 22:19:13
tags:
---
# 1.本地创建仓库：
- **首先进行初始化**
1.在桌面创建`mkdir 仓库名`
2.进入这个仓库`cd make`（在这里假设这个仓库名为make）
3.首先我们要初始化这个仓库，输入：`git init` 这是我们可以在make里看到一个.git的文件
4.现在我们创建一个html文件`touch from.html`（运行`git status -sb`查看文件状态，现在的mmm.html前面有？？问号）
5.然后我们先要把这个文件`git add mmm.html`添加到暂存区（现在我们再`git status -sb`查看一下文件状态，此时前面应该是 A，也就是我要把这些文件添加到仓库里去）
6.接下来我们`git commit -m "文件信息"`（将这个文件正式的提交至本地仓库）
7.你使用 `git log` 就可以看到历史上的变动
完成以上步骤，本地的仓库就创建完成了。

# 2.将本地仓库上传至GitHub
- 在GitHub上创建一个空仓库
![image.png](https://upload-images.jianshu.io/upload_images/11007474-c10d1686a0c533a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
***除了名字其他一律不填***
- 然后在Git中之前创建的仓库中运行如图画圈的两行命令（建议选择SSH地址）
![image.png](https://upload-images.jianshu.io/upload_images/11007474-04628131fe9d66a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/640)
然后刷新当前页面，你的仓库就上传到 GitHub 了！神不神奇？激不激动？

# 3. **下载 GitHub 上的仓库到本地**（刚开始建库在GitHub，然后下载，觉得这个好用）
- 创建及下载步骤
![image.png](https://upload-images.jianshu.io/upload_images/11007474-fc1fef603a4eba97.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
然后在这里获得下载链接（最好选择SSH下载地址）
![image.png](https://upload-images.jianshu.io/upload_images/11007474-60a48248d118f921.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)

1.git clone git@github.com:xxxx，下载仓库
2.git init，初始化本地仓库 .git
3.git status -sb，显示当前所有文件的状态
4.git add 文件路径，用来将变动加到暂存区
5.git commit -m "信息"，用来正式提交变动，提交至 .git 仓库
如果有新的变动，我们只需要依次执行 git add xxx 和 git commit -m 'xxx' 两个命令即可。
**先 add 再 commit，行了，你学会 git 了。**
6.git log 查看变更历史。
- **如何上传更新**
你在本地目录有任何变动，只需按照以下顺序就能上传：
`git add `文件路径
`git commit -m "信息"`
`git pull` （记得加上这个哦）
`git push`
下面是例子
```
cd git-demo-1
touch index2.html
git add index2.html
git commit -m "新建 index2.html"
git pull
git push
```
最好学会在VSCode里push，很方便！
<br/>

# 最后在这里交大家怎么删除GitHub上创建的库
1.首先点击你在GitHub里创建的仓库，点击settings
![image.png](https://upload-images.jianshu.io/upload_images/11007474-585fd7e9f3b225aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
2.点进去后，直接拉到最下方会看到一个 Delete this repository 点击它
![image.png](https://upload-images.jianshu.io/upload_images/11007474-a567bbde6837bb53.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/600)
3.在弹出的文本框里输入你的仓库名字，就可以删除了 So easy！  

<br/>
*待续*
