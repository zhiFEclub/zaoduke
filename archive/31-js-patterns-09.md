# JavaScript 模式之避免用eval 前端早读课第31期
![](http://upload-images.jianshu.io/upload_images/7219342-9698b103b7cd5be7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> If there are two or more ways to do something, and one of those ways can result in a catastrophe, then someone will do it.-- Edward A. Murphy(墨菲定律)

## 避免用eval
用 eval 让代码的可读性变差，也容易产出bug。用 eval 的性能也比较差。

用 `eval` 调用对象上的属性，属性的值是一个变量：
```
var property = "name";
alert(eval("obj." + property));
```

优化为：
```
var property = "name";
alert(eval(obj[property]));
```

setTimeout 或 setInterval 的第一个参数是字符串，相对于用 eval ：
```
setTimeout("myFunc()", 1000);
setTimeout("myFunc(1, 2, 3)"
```

优化为：
```
setTimeout(myFunc, 1000);
setTimeout(function () {
  myFunc(1, 2, 3);
}, 1000);
setTimeout(myFunc, 1000, 1, 2, 3); // IE 不支持这种写法
```

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《处理 Vue 单页面 Meta SEO的另一种思路》
### 背景
单页应用内容是动态生成的，搜索引擎的爬虫抓不到每个路由的信息，不利于SEO。如果对单页应用要做 SEO，一般会采用服务器端渲染（SSR）的方式。其实解决SEO问题不一定非得用服务端渲染来处理，服务端渲染对于刚接触 vue 的新手来说比较难。

### 概要
* 预渲染的介绍。预渲染为 SEO 提供了另一种可能，它能生成指定路由的静态页面。
* 预渲染的用法。预渲染插件： `prerender-spa-plugin` 和 `vue-meta-info` 的用法。
* 哪些场景不适合用预渲染。

阅读地址：https://zhuanlan.zhihu.com/p/29148760


往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
