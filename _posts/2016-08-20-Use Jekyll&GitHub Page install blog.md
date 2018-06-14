---
published: true
title: Use Jekyll&GitHub Page install blog
layout: post
author: alwaystiys 
category: Install
tags:
- Jekyll
---

使用GitHub Page和jekyll来搭建静态博客，
有GitHub免费空间的使用，顺便可以再深入下Git的使用。

在开始搭建个人博客之前也搜索许多相关的资料，每个人都有不同的方式，
后来发现还是官网的比较靠谱，所以大部分参照官网的教程搭建，
一路还算顺利，下面就记录下整个过程。 

#### 前言
下面简单扫盲下会用到的相关工具概念，具体的知识还得自己搜索下。

##### [Git](https://git-scm.com/)
简单的说 Git是一种版本控制系统。跟svn、cvs是同级的概念

##### [GitHub](https://github.com/) 
GitHub是一个网站，给用户提供Git服务。这样你就不用自己部署git系统，直接用注册个账号，用他们提供的git服务就可以。
Github是一个开源代码库及版本控制系统，它可以托管各种git库，号称程序员的Facebook，影响力非常大。

##### [GitHub Page](https://pages.github.com/)
Github里的Pages功能，就是用来为项目建立网站，使项目的展示能够简明易懂。我们就可以通过它来建立托管在Github上的静态网页。
Github Pages分为用户、组织、项目三种网站，我们的Blog要用到的是 User Pages site ，即用户网站。

##### [Jekyll](http://jekyll.bootcss.com/) 
Jekyll是一个简单免费的静态站点生成器，它根据网页源码生成静态文件，并且为我们提供了模板、插件。最关键的是可以免费部署在Github上。

##### 相关语言
* ruby
* markdown

#### 为什么会使用GitHub Page和jekyll搭建个人博客 
* 这二者都是开源免费的，可以自由定制网站风格
* Github给你提供了无限流量，世界各地访问速度都很理想，延迟基本在200ms以内
* 不管何时何地只要提交commit就能发布新文章，让博主专注于写文章
* 不需要数据库，通过markdown编写静态文章生成HTML页面，提升页面响应速度
* 享受git的版本管理功能，不用担心有文章丢失

#### 环境搭建

注：本文主要介绍windows环境下的安装。


##### 注册Github 
到[GitHub](https://github.com/)的官方网站，注册账户。
记住自己的用户名，后面会常用到。


##### 安装Git

安装[git for windows](https://git-for-windows.github.io/) 
安装后如果右键菜单出现如下选项就已经成功了。
[gitinstall.png](https://postimg.cc/image/wjlamo1b1/)

##### 创建自己的GitHub Page
以下参照了[GitHub Page官网的GitBub Page配置指南](https://pages.github.com/)，如果安装有问题可以查看原文。
创建自己的GitHub Page有三种类型：个人、组织或项目，下面只说明个人的方式：

1、首先必须已经在GitHub创建了自己的仓库，仓库名字为 yourusername.github.io

2、在本地创建一个目录作为自己的本地仓库，可以用自己喜欢的名字，my-jekyll-site-project-name

3、初始化本地仓库 git init my-jekyll-site-project-name

4、可能不熟悉本地Git和GitHub的关联的会有疑问，如果遇到问题，[参考这篇文章]()。

5、假定经过已经步骤仓库已经准备完毕，那么执行以下命令

```
cd my-jekyll-site-project-name
$echo "Hello World" > index.html
```
6、将本地仓库推送至GitHub
```
git add --all
~$git commit -m "Initial commit"
~$git push -u origin master
```
7、如果顺利进行，那么应该可以通过http://yourusername.github.io.访问得到你的GitHub Page主页。

8、打开网址后，你应该可以看到Hello World。个人GitBub Page就已经配置完毕了。接下来我们将配置本地Jekyll，配置成功后，本地可以执行测试，
如果将Jekyll生成的网址上传到GitHub，那么访问你的GItHub Page就可以看得到个人创建的博客了。

##### 安装Jekyll本地编译环境
下文假定了你已经会用一些基本Git操作，如果暂时不熟悉可以了解下基本语法。
以下参照了[GitHub Page官网的安装指南](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/#step-2-install-jekyll-using-bundler)，
如果安装有问题可以查看原文。


1、安装[Ruby](http://rubyinstaller.org/downloads/)
安装时注意勾选添加到环境变量PATH

2、官网安装推荐使用[Bundler](http://bundler.io/)
来管理Jekyll的安装以及使用。Bundelr用来管理Ruby的gem依赖，减少jekyll编译时的错误，
以及防止一些由于环境依赖产生的bug。安装Bundler之前，必须先安装Ruby。现在我们在第一步骤
已经安装后Ruby，下面我们安装Bundler。

```
$ gem install bundler

# 进入该目录
执行命令 cd my-jekyll-site-project-name

# 创建Gemfile文件，Ruby会使用这个目录的Gemfile来编译你的Jekyll网址
执行命令 touch Gemfile

# 用编辑器打开Gemfile文件，比如Sublime Text，把下面两行代码加入Gemfile文件
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins

# Install Jekyll and other dependencies from the GitHub Pages gem:
执行命令 bundle install
该过程可能需要翻墙，时间可能会比较长，如果顺利的话可以看到如下输出结果：
Fetching gem metadata from https://rubygems.org/............
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Resolving dependencies...

```

3、经过上面的步骤后，基本就完成了Jekyll的配置，可以通过如下命令创建一个jekyll基本模板博客。
```
bundle exec jekyll new . --force
```

4、在本地博客的目录下，执行命令：
```
bundle exec jekyll serve
```

5、之后，在浏览器访问http://localhost:4000，就可以看到博客了。

6、如果喜欢自己自定义自己的博客样式，那么可能要再学习下jekyll的语法等。
或者只是想撰写文章，想快速搭建自己的博客样式，那么可以到[Jekyll模板网址](http://jekyllthemes.org/)
浏览有没有自己喜欢的样式，并且下载下载，替换到自己的本地目录下，简单修改下配置就可以运行了。
