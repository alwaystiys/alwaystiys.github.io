---
published: true
title: Compile Quake3 Code and Run
layout: post
author: alwaystiys 
category: Game
tags:
- Quake
---

##### 下载Q3源代码以及Q3游戏安装包
- 从Id Software的GitHub上下载Quake3源代码。[点击下载地址](https://github.com/id-Software/Quake-III-Arena)
- 因为源代码不包含任何资源文件，所以为了能够运行游戏，还需要下载Q3游戏安装包。安装包我已经放在我自己的百度网盘上，需要自行前往下载。[安装包地址](http://pan.baidu.com/s/1gfdUrBl)，[安装包补丁地址](http://pan.baidu.com/s/1nvItCwD)
<!-- more -->
##### 编译Q3源代码以及运行游戏
- 安装Q3游戏安装包到自己指定的或默认的路径下（比如我的是F:\Game\quake3）。并安装1.32补丁（含主程序和数据库，直接覆盖在安装目录内）。
- 解压Q3源代码压缩包，使用vs2012（我自己的电脑用的vs版本是2012）打开quake.sln工程，提示代码升级是点击确定升级到2012支持格式。
- 以DEBUG模式编译解决方案中的8个工程（我是按顺序编译），没问题的话，应该是都编译通过。
- 在quake3工程的属性页面，点击Debugging page标签，改变Wroking Directory为$(TargetDir)，Command Arguments 设置参数为+set sv_pure 0 +set vm_game 0 +set vm_cgame 0 +set vm_ui 0 "F:\Game\quake3"
- 将Quake3设置为启动项目，然后点击F5。
- 如果步骤没问题，应该可以看到Q3游戏已经启动运行。