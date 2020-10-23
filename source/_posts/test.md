---
title: 測試
date: 2020-09-02 21:01:01
tags: 架設Hexo

---
測試發文~~~~~
![github:pages x hexo](https://cdn0-t17.techbang.com/system/attached_images/2019/07/261667/original/f83071ffb726a0af8c3470cea40cde57.png)

github-hexo 如何添加自定義網頁
Hexo自定义原理
Hexo 系列的博客中的文章都是经Hexo的主题渲染的静态网页。所以Hexo博客大部分都呈现出一种高度的统一化与规范化。不过 Hexo 提供了跳过渲染功能，使得我们可以直接在博客中放入自定义网页。
比如在博客中放入图片、自定义404.html、自定义About页面、简历等
创建自定义网页，网页可以是自己编写的，也可以是别人现成的源码（下载喜欢的页面）。
网页编写完成后，在Hexo\source目录下创建一个文件夹（文件夹名称任意，比如我创建的是about这个文件夹，部署完成后，访问http://mrlsm.github.io/about
即可看到效果，依此类推）
将 html 文件放置于此文件夹，并重命名为 index.html 。
跳过渲染
跳过渲染有下述两种方法：
1. 在html文件中添加跳过渲染指令
> 用编辑器打开放入\Hexo\source\创建的文件夹中的 index.html 文件，在开头添加如下代码即可

``` bash
---
layout: false
---
```
添加该指令后，执行 hexo g命令时便会跳过该 index.html文件，使得index.html不受当前 hexo 主题影响，完全是一个独立的网页，如果网页引用了 css 或 js，css 和 js 需使用外链或者将css js 文件放入index.html同目录下引用。
2. 在_config.yml文件中设置skip_render
使用编辑器打开 Hexo 目录下的_config.yml文件，找到skip_render
skip_render一般有以下四种常用参数：
``` bash
跳过source目录下的 test.html: skip_render: test.html

跳过source目录下 test 文件夹内所有文件：skip_render: test/*

跳过source目录下 test 文件夹内所有文件包括子文件夹以及子文件夹内的文件：skip_render: test/**
```
跳过多个路径：
``` bash
skip_render:
 - test.html
 - test/*
```
3.完成
执行hexo g -d 发布，就可以在自己的网页上看到自定义页面了（可以制作一份自己的简历哦）。

未來可參考
[Hexo 安裝教學、心得筆記](https://wwssllabcd.github.io/blog/2014/12/22/how-to-install-hexo/#%E5%8A%A0%E5%85%A5-Google-Analytics)
提供google分析 評論 等 安裝功能

[HEXO 連結其他文章](https://github.com/iissnan/hexo-theme-next/issues/978)

目前大體上是參考
- 1. https://medium.com/@z0935323866/%E7%AC%AC%E4%B8%80%E6%AC%A1%E6%9E%B6%E8%A8%ADhexo%E7%B6%B2%E7%AB%99-7074161158f8
以及
- 2. https://medium.com/@bebebobohaha/%E4%BD%BF%E7%94%A8-hexo-gitpage-%E6%90%AD%E5%BB%BA%E5%80%8B%E4%BA%BA-blog-5c6ed52f23db
這2篇文章做交互參照

https://ed521.github.io/2019/07/hexo-install/ 這篇有些註解寫的還行 有空再參閱
更换Hexo的网页图标/小图片Hexo change page favicon https://wangxiaoyu-go.github.io/2018/11/18/change-theme-favicon/

長期目標：https://magicdogguo.github.io/  
長得像這位的
