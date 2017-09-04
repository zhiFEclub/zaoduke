# JavaScript 模式之单var模式 前端早读课第26期
![](http://upload-images.jianshu.io/upload_images/7219342-ea9d29aee5fad30c.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 即使生活给你一千个伤心的理由，你也要找一千零一个开心的借口。

## 单 var 模式
> 在函数里，集中用一个 var 来声名该函数会用到的所有变量。

### 优势
1. Provides a single place to look for all the local variables needed by the function
2. Prevents logical errors when a variable is used before it's defined
3. Helps you remember to declare variables and therefore minimize globals
4. Is less code (to type and to transfer over the wire)

挑重点：集中声名变量会减少忘记声名变量就使用变量的可能性。如果没声名就使用，会导致变量为全局变量。

### 写法
```
function func() {
  var a = 1
    , b = 2
    , sum = a + b
    , myobject = {}
    , i
    , j;
  // function body...
}
```

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《写CSS的姿势》
### 概要
介绍了写 CSS 的各种姿势：
* 直接写 CSS，不采用任何的 CSS 处理器
* 通过 CSS 处理器写，然后在编译出 CSS
* 直接写 CSS，通过PostCSS再处理
* 通过处理器编译出CSS，再使用 PostCSS 二次加工
* CSS in JavaScript

阅读地址：http://www.w3cplus.com/css/css-evolution.html

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d