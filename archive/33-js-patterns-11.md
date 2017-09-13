# JavaScript 模式之尽可能少用全局对象 前端早读课第33期
![](http://upload-images.jianshu.io/upload_images/7219342-764227057271d25b.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> A：借我1000块。B：拿去，1024，我给你凑了个整儿。

本期编辑： [Nicole_tiny](http://www.jianshu.com/u/7b75d8681776)。

## 尽可能少用全局对象
看如下代码
```
myglobal = "hello"
var myglobal2 = "hello"
console.log(myglobal); // "hello"
console.log(window.myglobal); // "hello"
console.log(myglobal2); // "hello"
console.log(window.myglobal2); // "hello"
```

上面的代码定义了全局变量。全局变量会让代码容易出错。比如，页面上多个 js 文件会异步的给同一个全局变量赋值，你能知道最后变量的值是什么吗？

优化写法:
```
(function() {
  var myglobal = "hello"
  console.log(myglobal) // "hello"
  console.log(window.myglobal) // undefined
})()
```

注意：定义变量要用 `var`，如果忘了加，会导致变成全局变量。

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/ 。JavaScript 的通用模式分享完喽，明天开始分享 jQuery 相关模式~

## 文章推荐
## 《一道面试题目引发的思考》
### 背景
多列布局是前端一个经典的反复被提及的面试题目，最典型的即两列，左列定宽菜单栏，右列变宽为内容区域。对于此题通常得到的答案无外乎左列浮动定宽，然后右列或浮动，或设置外边距，或绝对定位等等。而设置右列overflow属性的答案也是一个比较好的思考方向。

### 概要
* overflow属性
* overflow属性跟布局的关系
* 为什么overflow非visible值会触发BFC?

阅读地址：https://juejin.im/post/59b225e7f265da24797b9974

相关阅读：[学习BFC](https://juejin.im/post/59b73d5bf265da064618731d)

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
