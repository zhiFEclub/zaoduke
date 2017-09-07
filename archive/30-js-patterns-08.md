# JavaScript 模式之避免隐式的类型转化 前端早读课第30期
![](http://upload-images.jianshu.io/upload_images/7219342-bd5346ef5847ce80.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 一个人静静坐在电脑面前写代码的感觉，那是什么感觉?那是武林高手闭关修炼的感觉。

## 避免隐式的类型转化
用 `==` 来判断值是相等，会做隐式的类型转化。如
```
0 == false // 0 转化成布尔值为 false。所以结果是 true。
```

隐式的类型转化会让代码的运行变得不可预期。如
```
[] == 0 // 猜猜结果是 true 还是 false？
```

用`===` 来判断值是相等，不会做隐式的类型转化。所以，判断值相等要用 `===` 代替 `==`。

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《asm.js 和 Emscripten 入门教程》
### 背景
Emscripten 可以将 C / C++ 代码编译成一种叫 asm.js 的 JavaScript 变体。由于 asm.js 的运行速度较快，所以一些计算密集型的操作（比如计算 Hash）可以使用 C / C++ 实现，再在 JS 中调用它们。

### 概要
* asm.js 和 Emscripten 的介绍和基本用法。
* asm.js 的用途。

阅读地址：http://www.ruanyifeng.com/blog/2017/09/asmjs_emscripten.html


往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
