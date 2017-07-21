---
layout: post
cover: 'assets/images/cover7.jpg'
title: Sass的表达式和控制命令　if篇
date:   2014-07-22 2:03:35
tags: fables fiction
subclass: 'post tag-test tag-content'
categories: 'casper'
navigation: True
logo: 'assets/images/ghost.png'
---




<br><br>
### if()
if() 是 Sass 的一个内建函数，与之相似的 @if 则是一个内建指令。if() 用来做条件判断并返回特定值，示例如下:
```

@mixin test($condition){
  $color: if($condition,blue,red);
  color:$color;
}

.First{
  @include test(true);
}
.Second{
  @include test(false);
}

```

*编译结果为:*

```

.First {
  color: blue; }

.Second {
  color: red; }

```
>  在上面的例字中，if() 函数内的三个参数分别代表: *测试条件*，*测试成功返回值*，*测试失败返回值*\
（除了 false 和 null 之外的所有测试条件都被视为测试成功）。如果使用数字作为上述示例的条件，同样会返回测试成功的值:

### @if
*@if 后跟一个表达式，如果表达式的结果为 true，则返回特定的样式，示例如下:*

```

@mixin txt($weight) {
  color: white;
  @if $weight == bold { font-weight: bold;}
}

.txt1 {
  @include txt(none);
}

.txt2 {
  @include txt(bold);
}
```
*编译结果为:*
```

.txt1 {
  color: white; }

.txt2 {
  color: white;
  font-weight: bold; }

```
*此外，我们可以使用 @if ... @else if ... @else 结构来处理多个条件，示例如下：*

```

@mixin txt($weight) {
  color: white;
  @if $weight == bold { font-weight: bold;}
  @else if $weight == light { font-weight: 100;}
  @else { font-weight: normal;}
}

.txt1 {
  @include txt(bold);
}

.txt2 {
  @include txt(light);
}

.txt3 {
  @include txt(none);
}

.txt4 {
  @include txt(normal)
}

```
*编译结果如下:*
```

.txt1 {
  color: white;
  font-weight: bold; }

.txt2 {
  color: white;
  font-weight: 100; }

.txt3 {
  color: white;
  font-weight: normal; }

.txt4 {
  color: white;
  font-weight: normal; }

```
这里的 <code>.txt3 </code>和<code> .txt4</code> 是用来向各位演示 @if 的解析机制。在 <code>.txt1 </code>中，如果不传入 <code>bold</code>，那么就不会生成 <code>font-weight</code> 相关的样式。
