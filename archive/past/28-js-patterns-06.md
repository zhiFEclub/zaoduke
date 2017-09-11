# JavaScript 模式之内置对象的原型 前端早读课第28期
> 软件和教堂非常相似——建成之后我们就在祈祷。

## 不在内置对象的原型上新增方法
### 写法
```
if (typeof Object.prototype.myMethod !== "function") {
  Object.prototype.myMethod = function () {
    // implementation...
  };
}
```

内置对象的原型上新增方法会降低代码的可维护性，让代码变得不可预测。如果要写一些内置对象的工具方法，用将对象做为参数传入的方式，如
```
function arrayEvery(array) {...}
```

Underscore.js 就是这么做的。

例外：只有在旧浏览器上实现新浏览支持的原型方法时，才在内置对象的原型上新增方法。如：
```
// some 是 ES6 中新出的方法。
if (typeof Array.prototype.some !== "function") {
  Array.prototype.some = function () {
    
  };
}
```

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《【深度长文】JavaScript数组所有API全解密》
### 背景
数组是一种非常重要的数据类型，它语法简单、灵活、高效。 在多数编程语言中，数组都充当着至关重要的角色，以至于很难想象没有数组的编程语言会是什么模样。特别是JavaScript，它天生的灵活性，又进一步发挥了数组的特长，丰富了数组的使用场景。可以毫不夸张地说，不深入地了解数组，不足以写JavaScript。

### 概要
系统讲解了JavaScript数组的各种特性和API。包含了 ES6 新增一些新特性。

阅读地址：http://louiszhai.github.io/2017/04/28/array/


往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
