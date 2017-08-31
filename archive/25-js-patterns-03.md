# JavaScript 模式之获得全局对象 前端早读课第25期
![](http://upload-images.jianshu.io/upload_images/7219342-8af9dc93e81a64bc.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 每一件绝世无双的好作品都是以无比寂寞的勤奋为前提,要么是血,要么是汗,要么是大把曼妙的青春时光。

## 获得全局对象
> 不用硬编码的方式获得全局对象。

### 写法
```
var global = (function () {
  return this || (1, eval)('this');
}());
```

上面代码的通用性很强：不仅能在浏览器环境中，获得浏览器的全局对象 `window`，还能在 Node.js 的环境中获得 Node.js 的全局对象。上面的代码兼容 ES3, ES5 和 ES5 严格模式。

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《简单学正则》
### 背景
> 正则表达式是一组由字母和符号组成的特殊文本, 它可以用来从文本中找出满足你想要的格式的句子.

正则比较难学，而且还博大精深 XD。  

### 概要
* 什么是正则
* 基本匹配
* 元字符
* 简写字符集
* 前后关联约束(前后预查)
* 标志

阅读地址：https://github.com/zeeshanu/learn-regex/blob/master/README-cn.md

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d


