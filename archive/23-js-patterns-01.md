# JavaScript 模式之函数表达式模式 前端早读课第23期
> 这个世界上只有10种人：懂二进制的和不懂二进制的。

本期编辑： [bestswifter](http://www.jianshu.com/u/3e55748920d2),[九彩拼盘](http://www.jianshu.com/u/EhUmA3)。

## 函数表达式模式
> 将匿名函数赋值给变量。

### 优势
1. Makes it easier to understand "functions as an object".
2. It enforces good semicolon habits.
3. Doesn't have much of the baggage traditionally associated with functions and scope.

尝试翻译的比较搓，就看原文吧。

### 写法
```
var getData = function () {
}
```

在代码报错时，为了方便调试：能在调用堆栈中看到函数的名字。可以给函数起个名字: 
```
var getData = function getDataF () {
}
```

注意：上面代码中，如果变量名和函数名是一样的话，在 IE 和 coffeescript 可能会有问题，具体见[这里](https://github.com/jashkenas/coffeescript/issues/366)。

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《浅谈 JavaScript 模块化编程》

### 背景
随着越来越多的JavaScript库和框架的出现，SPA的流行以及Node.js的迅猛发展，如果我们还不对自己的JS代码进行一些模块化的组织的话，开发过程会越来越困难，运行性能也会越来越低。因此，了解JS模块化编程是非常重要的。

### 概要
* 模块的定义
* AMD 和 CMD 规范
* Require.js 和 Sea.js

阅读地址：https://segmentfault.com/a/1190000000492678