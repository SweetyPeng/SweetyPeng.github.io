---
title: 关于Git使用一些记录
date: 2018-08-14 16:56:35
tags: [git]
categories: Git操作系列
---
## 关于Git使用的一些记录
1. 在朋友的强烈安利下，抛弃了sublime，使用VS code。对于git的操作，比命令行 会 方便 些。
2. ### 解决向gitlab/github 提交代码总是提示输入用户和密码

```
$ git config --global credential.helper store
 
```
 下一次操作后再一次输入用户名和密码 ，之后就不用了。
 
```
[credential]
        helper = store
```
直接在 用户目录下的.git 下的 .config 文件下添加这些字段，也能行的通。
<!--   MORE  -->
3. ### 常用命令

```
$ git add
$ git commit -m "注释" 
```
每次修改，如果不用git add到暂存区，那就不会加入到commit中

```
$ git branch 分支名  //新建分支
$ git checkout 分支名 //切换分支
```
查看分支 直接 git branch;   
checkout 有不同的用法，待使用中进一步了解。

```
$ git branch -d <分支名> //删除本地分支 
$ git push origin --delete <分支名> //删除远程分支 
```
个人理解，本地操作与远程操作中的区别就是 有没有 origin

#### 合并分支
把 A 合并到 B 上，
所以 应该是 在 B 分支 上 git merge A 。

这个操作还是不够熟练 ，出现冲突，总是出错。

4. 可参考文献
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000 廖雪峰git教程（有点深，初看的有点迷）