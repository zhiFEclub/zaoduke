# JavaScript 模式之条件 前端早读课第24期
![](http://upload-images.jianshu.io/upload_images/7219342-69b8c349f25638b3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 任何你写的代码，超过 6 个月不去看它，当你再看时，都像是别人写的。

本期编辑： [小虫巨蟹](http://www.jianshu.com/u/7233332cb959)，[九彩拼盘](http://www.jianshu.com/u/EhUmA3)。

## 条件语句的写法
常规写法
```
if (type === 'foo' || type === 'bar') {
}
```

写法1:用正则
```
if (/^(foo|bar)$/.test(type)) {
}
```

写法2:用对象
```
if (({foo:1, bar:1})[type]) {
}
```

对于上面的3种写法。  

1. 常规写法的性能比用正则好。
1. 在条件判断数量（数量小于5）比较少的情况下，常规写法比用对象快。条件多的情况下，用对象更快。

具体的benchmark 见[这里](https://jsperf.com/if-this-or-that)

常规写法
```
if (value == 0) {
  return result0;
} else if (value == 1) {
  return result1;
} else if (value == 2) {
  return result2;
} else if (value == 3) {
  return result3;
} else if (value == 4) {
  return result4;
} else if (value == 5) {
  return result5;
} else if (value == 6) {
  return result6;
} else if (value == 7) {
  return result7;
} else if (value == 8) {
  return result8;
} else if (value == 9) {
  return result9;
} else {
  return result10;
}
```

优化写法:用二分法
```
if (value < 6) {
  if (value < 3) {
    if (value == 0) {
      return result0;
    } else if (value == 1) {
      return result1;
    } else {
      return result2;
    }
  } else {
    if (value == 3) {
      return result3;
    } else if (value == 4) {
      return result4;
    } else {
      return result5;
    }
  }
} else {
  if (value < 8) {
    if (value == 6) {
      return result6;
    } else {
      return result7;
    }
  } else {
    if (value == 8) {
      return result8;
    } else if (value == 9) {
      return result9;
    } else {
      return result10;
    }
  }
}
```

判断值是数字的常规写法
```
if (value == 0) {
  return result0;
} else if (value == 1) {
  return result1;
} else if (value == 2) {
  return result2;
}
```

优化写法: 用数组
```
var results = [result0, result1, result2];
return results[value];
```

对于 if 内容只有一行内容的简写
```
var 
      type = 'foo',
      type2 = 'bar',
      result = 0;
      
type == 'foo' && result++;
console.log(result); // 1
!type == 'foo' || result++;
console.log(result); // 2
type == 'foo' && type2 == 'bar' && result++;
console.log(result); //3
type == 'foo' && type2 == 'bar' && result == 3 && (result=0)
console.log(result); //0
type == 'OOF' || result++; //equivalent: type != 'OOF' && result++;
console.log(result); //1
```

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《Vue 组件间的样式污染》
### 背景
Vue 组件的组件化写法符合 web component 这种面向未来的规范，然而在样式隔离方面，它依然有一点美中不足。

### 概要
1. 污染是如何产生的？
2. 增加 Scoped 标识
3. ScopeId 的继承
4. 怎么破？
5. 这应当属于 Vue-loader 的一个 bug

阅读地址：http://www.jianshu.com/p/b7292d01c361


