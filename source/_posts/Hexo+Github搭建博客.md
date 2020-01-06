---
title: 使用Hexo+Github搭建个人博客
date: 2018-06-06 11:24:20
tags: [hexo,github,blog]
categories: hexo博客使用系列
---
之前看到别人炫酷的博客很是羡慕，于是心痒痒，就想着自己也拥有一个。在上一次没捣鼓出来之后，这一次，神奇地一切进展顺利，让我开心了一把。
趁着记忆温热，赶紧记录一下这来之不易的成果。<br/>
期间参考了CSDN各种技术帖，感谢各位大佬们的技术参考！
<!--   MORE  -->
## 环境搭建
1. node.js 
2. git
<br>这两个直接可以在官网上下载安装
3. hexo
<br>1）在本地先建一个文件夹，存放。
<br>2）在新建的目录下，右键 git bash here
<br>3）命令行：$ npm install -g hexo

### 注意
- github上仓库 使用 名字.github.io
- 测试安装：node -v、 npm -v、 git  -v 显示版本号
## 过程
hexo命令使用
1. 初始化：$ hexo init
2. 生成静态资源：$ hexo g  （注释：g -->generate)
3. 启动服务，本地预览： $ hexo s  ( s-->server)
4. 上传: $ hexo d ( d-->deploy)
5. 清除打包文件： $ hexo clean

hexo部署
1. 安装部署插件  
```
npm install hexo-deployer-git --save
```

2. 修改站点目录下的_config.yml文件，修改deploy下的配置如下：

```
deploy:
  type: git
  repository: 此处仓库clone然后ssh复制过来的地址
  branch: master

```
3.使用前面的命令，就能初步看到博客了。
## 主题
系统默认给的landscape，还默认给了 hello-world.md 可以预览

我觉得最炫酷的就是Next主题了，于是我就换主题了。
在换主题这里，算是坎坷了一下。

### 重点说这个背景

#### 修改_layout.swig
打开 next/layout/_layout.swig
在 < /body>之前添加代码(注意不要放在< /head>的后面)

```
{% if theme.canvas_nest %}
<script type="text/javascript" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}
```
#### 修改配置文件
打开 /next/_config.yml,在里面添加如下代码：(我直接扔在最后面了，效果出来了就不管辣么多了)

```
# --------------------------------------------------------------
# background settings
# --------------------------------------------------------------
# add canvas-nest effect
# see detail from https://github.com/hustcc/canvas-nest.js
canvas_nest: true
```
运行 hexo clean，然后运行 hexo g,然后运行 hexo s 哈哈哈，就看到了。

#### 注意点
1. 下载Next主题的时候，没有理解意思，导致折腾了好久。<br/>
$ git clone 主题地址 themes/next
（themes/next-->这里是指在本地的位置）

1. 站点配置文件_config.yml，修改

```
theme: next
```
==在所有的里面，千万不要忘了冒号后面的空格！！！吃过亏就知道了！==

## 最后

对于markdown使用，还是有困难.<br/>
对于Next主题的更多个性化操作，还有待进一步学习~
<br> 
**真心敬佩那些技术大神，太牛逼了！**