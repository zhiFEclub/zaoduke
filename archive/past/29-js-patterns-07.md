# JavaScript 模式之 switch 前端早读课第29期
![](http://upload-images.jianshu.io/upload_images/7219342-bf4bf064b1108655.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 傻瓜都能写出计算机能理解的程序。优秀的程序员写出的是人类能读懂的代码。

本期编辑： [Nicole_tiny](http://www.jianshu.com/u/7b75d8681776),[九彩拼盘](http://www.jianshu.com/u/EhUmA3)。

## switch 模式
用 switch 写出可读性好，健壮的代码。这么写：
```
var inspect_me = 0,
    result = '';
switch (inspect_me) {
case 0:
  result = "zero";
  break;
case 1:
  result = "one";
  break;
default:
  result = "unknown";
}
```

要注意如下几点：

1. case 和 switch 对齐。代码有合适的缩进。
1. 每个 case 后面都要有 break。
1. 如果有需求几个 case 公用代码（不加 break），需要专门写注释说明，否则会被认为是漏写了 break。
1. switch 必须以 default 结尾来处理一些未知情况。

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《前端性能优化之 DOM 篇》
### 概要
* DOM的定义
* DOM性能优化涉及的方面
* 优化HTML的结构
* 浏览器的工作原理
* 如何避免触发重绘和回流

阅读地址：http://fsux.me/%E9%9A%8F%E7%AC%94/%E6%9E%B6%E6%9E%84/%E6%B5%85%E8%B0%88%E5%89%8D%E7%AB%AF/2017/04/13/Front-end-performance-optimization-dom.html

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
