---
title: Hexo+Github之更换电脑后如何继续使用
date: 2018-09-08 13:24:20
tags: [hexo,github,blog]
categories: hexo博客使用系列
---
## 前言
之前经过一番折腾，终于利用hexo和github pages 完成了自己的博客。一切本来都是如此美好，然后意外发生了。前不久自己的电脑坏了，于是申请了公司的电脑。当准备写博客的时候，一下子愣住了。该怎么继续呢···
<!--   MORE  -->
试图把github中的克隆到本地，不用说，肯定不行的，因为当初只是参考步骤 通过hexo deploy 部署到的github上，也没有考虑到后面会发生那么多意外。

所以无可奈何，又重新开始了一次新的折腾。那么，这一次，就留好“后路”。

## 创建分支，保存环境
之前直接通过deploy到name.github.io仓库master中的文件，就是生成的静态的html文件，可是自己的博客主题环境以及md文件这些，是留在电脑本地的，所以，为了下一次的方便，必须要来个备份啊~

所谓的“备份”，就是在博客对应的仓库中 新建一个分支 hexo ，用来保存源文件，而master负责的是hexo编译后的博客文件。

需要备份的文件：
文件 | 说明
---|---
 scaffolds/| 博客文章的模板
source    | 所有博客文章，以及about、tags、categories等page
themes/ | 主题
.gitignore | 在push时需要忽略的文件和文件夹
_config.yml | 站点配置文件
package.json | 依赖包的名称和版本号

### 注意点
- .gitignore文件

```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```
- _config.yml文件

```
deploy:
    type: git
    repo: https://github.com/SweetyPeng/SweetyPeng.github.io
    branch: master
```
master分支的文件,是通过Hexo进行管理，设置branch为master，deploy生成的html静态文件会自动保存在master中。

- next主题

使用的主题如果是从GitHub克隆的，那么主题文件夹下有Git管理文件，需要将它们移除。不然保存不了，这一点深深吃亏，每次都重新配置主题，作死！
```
$ rm -R themes/next/.git*
```
## 更换电脑后的使用
1. git clone 拷贝仓库，默认是hexo分支
2. 在刚拷贝下的本地文件夹中，通过git bash 命令，依次进行`npm install hexo`、`npm install`、`npm install hexo-deployer-git`
（注意，不需要hexo init这条指令，hexo init 会初始化 Hexo 环境, 该操作会清空.git 文件夹, 导致版本控制信息会丢失，一切就白费了）
3. 然后就可以愉快的一如既往地记录博客了~


