---
layout: post
cover: 'assets/images/cover3.jpg'
title:  如何在laravel 项目中运用基于bootstrap Sass文件结构 编译自己的Sass文件
date:   2017-07-22 1:33:49
tags: test content
subclass: 'post tag-test tag-content'
categories: 'casper'
navigation: True
logo: 'assets/images/ghost.png'
---


##### 什么是 Sass ?

SASS是一种CSS的开发工具，提供了许多便利的写法，大大节省了设计者的时间，使得CSS的开发，变得简单和可维护。 本文总结了在项目中bootstrap Sass如何编译。我的目标是，有了这篇文章，日常的一般使用就不需要去看官方文档了。

##### 安装

SASS是Ruby语言写的，但是两者的语法没有关系。不懂Ruby，照样使用。只是必须先安装Ruby，然后再安装SASS。

##### 首先进入<code>bootstrap</code>官网


> [下载bootstrap Sass链接](http://v3.bootcss.com/getting-started/)

下载好以后解压完目录,我们只需要吧　<code>assets</code>　这个目录放到项目public下面,文件目录结构图:


![assets目录.png](http://upload-images.jianshu.io/upload_images/5982972-957bd37fa3aaf5e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


然后点开　<code>stylesheets</code>　文件夹,我们会看到文件夹名字前面都有下划线,这么一个梗,<code>代表文件不能被编译</code>,好我们继续往下看,bootstrap sass 结构

> 在 /assets/stylesheet/中，bootstrap文件夹和bootstrap.scss,bootstrap-compass都是我们核心文件。
> 点开_bootstrap.scss文件　我们会看到以下目录

```

/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */

// Core variables and mixins
@import "bootstrap/variables";  
@import "bootstrap/mixins";

// Reset and dependencies
@import "bootstrap/normalize";
@import "bootstrap/print";
@import "bootstrap/glyphicons";

// Core CSS
@import "bootstrap/scaffolding";
@import "bootstrap/type";
@import "bootstrap/code";
@import "bootstrap/grid";
@import "bootstrap/tables";
@import "bootstrap/forms";
@import "bootstrap/buttons";

// Components
@import "bootstrap/component-animations";
@import "bootstrap/dropdowns";
@import "bootstrap/button-groups";
@import "bootstrap/input-groups";
@import "bootstrap/navs";
@import "bootstrap/navbar";
@import "bootstrap/breadcrumbs";
@import "bootstrap/pagination";
@import "bootstrap/pager";
@import "bootstrap/labels";
@import "bootstrap/badges";
@import "bootstrap/jumbotron";
@import "bootstrap/thumbnails";
@import "bootstrap/alerts";
@import "bootstrap/progress-bars";
@import "bootstrap/media";
@import "bootstrap/list-group";
@import "bootstrap/panels";
@import "bootstrap/responsive-embed";
@import "bootstrap/wells";
@import "bootstrap/close";

// Components w/ JavaScript
@import "bootstrap/modals";
@import "bootstrap/tooltip";
@import "bootstrap/popovers";
@import "bootstrap/carousel";

// Utility classes
@import "bootstrap/utilities";
@import "bootstrap/responsive-utilities";


```


**注! 不要再bootstrap 文件下写自己的scss文件,可以再同级下创建一个文件夹如:myselfBooStrap，从而编写自己的scss文件**

  1. 编写自己的scss 文件前缀要和bootstrap一样,统一加上下划线如　_demo.scss.

  2. 我们编写完sass代码，如何引入呢? 如下:加入一条关键性代码.
 <pre>@import "myselfBooStrap/demo";</pre>
  3. 然而还没完,仔细看 stylesheets 下的scss文件前面也有_下划线,ok.把项目文件名前的_去掉
  4.  Sass　编译命令 : sass 编译的文件名　(编译路径)编译的文件名　　(命令如下)
 <pre> sass bootstrap.min.scss ../css/bootstrap.min.css </pre>
 5.现在就有个疑问了,我每次编写代码,每次都得输一次命令吗? No　不需要, 文件自动监听,上代码:

  <pre>sass --watch bootstrap.min.ss:../css/bootstrap.min.css</pre>

  > ok ！　尽情的享受sass　带来的。。。。　
