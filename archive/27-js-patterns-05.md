# JavaScript 模式之循环的优化 前端早读课第27期
> Talk is cheap. Show me the code.

## 模式
## 循环数组的优化
常规写法
```
for (var i = 0; i < myarray.length; i++) {
  // do something with myarray[i]
}
```

优化方式:缓存循环次数。
```
var i = 0,
    max,
    myarray = [];
for (i = 0, max = myarray.length; i < max; i += 1) {
  // do something with myarray[i]
}

```

或
```
var i, myarray = [];
for (i = myarray.length; i--;) {
  // do something with myarray[i]
}
```

或
```
var myarray = [],
    i = myarray.length;
while (i--) {
  // do something with myarray[i]
}
```

## 遍历对象(for-in)的优化
有下面的对象
```
var man = {
  hands:2,
  legs:2,
  heads:1
};
```

遍历的一般写法
```
for (var i in man) {
  console.log(i, ":", man[i]);
}
```

优化方式，遍历时排除原型上的属性
```
for (var i in man) {
  if (man.hasOwnProperty(i)) { // filter
    console.log(i, ":", man[i]);
  }
}
```

或
```
for (var i in man) {
  if (Object.prototype.hasOwnProperty.call(man, i)) { // filter
    console.log(i, ":", man[i]);
  }
}
```

或
```
var i,
    hasOwn = Object.prototype.hasOwnProperty;
for (i in man) {
  if (hasOwn.call(man, i)) { // filter
    console.log(i, ":", man[i]);
  }
}
```

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《强力推荐！那些你不能错过的 GitHub 插件和工具》
### 背景
以代码托管平台起家的 GitHub 网站，已然成为全球程序员工作和生活中不可或缺的一份子。从优秀的企业，到优秀的程序员，都将自己最优秀的代码作品存放在这片开源净土里，供彼此学习交流。

既然 GitHub 这么重要，又被我们使用得这么频繁，那关于 GitHub 的一些优秀浏览器插件或者其他工具，我们就一定不可错过啦。

### 概要
推荐的一堆 GitHub 的插件。

阅读地址：https://juejin.im/post/59ade28051882538fd72fa2c

我做为 GitHub 的重度用户，只用过 Octotree，惭愧啊。感觉去找几个下个玩玩~

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
