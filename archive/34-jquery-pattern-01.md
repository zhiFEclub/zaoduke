# jQuery 模式上篇 前端早读课第34期
![](http://upload-images.jianshu.io/upload_images/7219342-6bd0d8542f28cf6f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

> 按代码行数来评估软件开发的进度，就如同按重量来评估飞机建造的进度。

## 链式调用
```
$(document.body).append("<div class='baaron' />");
$("div.baaron").click(function () {
});
```

用链式调用能避免再查询。推荐写法：
```
$("<div class='baaron' />")
    .appendTo(document.body)
    .click(function () {
    });
```


### 一次性设置元素的内容
```
$.each(reallyLongArray, function (count, item) {
  var newLI = '<li>' + item + '</li>';
  $('#ballers').append(newLI);
});
```

DOM 操作是比较耗性能的。上面的代码，每次循环，都会做一次 DOM 操作。用拼接字符串的方式一次性设置元素的内容来减少 DOM 操作。写法如下
```
var myhtml = '';
$.each(reallyLongArray, function (count, item) {
  myhtml += '<li>' + item + '</li>';
});
$('#ballers').html(myhtml)
```

也可以用 `createDocumentFragment`，这里就不介绍了。

## 使用 data
```
$(elem).data(key, value)
```

推荐写法
```
$.data(elem, key, value)
```

推荐写法的效率比反模式高。

## 查找子元素
查找子元素用 find 比用上下文的代码可读性好。性能方面差不多。  
用上下文这么写：
```
var arms = $('div.robotarm', '#container');
$('.reply_form', $(this).closest('.comment')).hide();
```

用 find 这么写
```
var arms = $('#container').find('div.robotarm');
$(this).closest('.comment').find('.reply_form').hide();
```

## 分离元素
如要要对元素做大量操作，将元素从 DOM 树中分离出来，操作完后再放回去。很多 DOM 操作会导致页面的重绘，将元素分离出去可以减少重绘，从而提升性能。如

```
var table = $('#some-table');
var parent = table.parent();
table.detach();
table.addLotsAndLotsOfRows(); 
parent.append(table);
```

## 事件委托
```
$('a.trigger', $('#container')[0]).live('click', handlerFn)
```

如上写法不支持链式调用。推荐写法
```
$('#container').on('click', 'a.trigger', handlerFn);
```

## 缓存查询结果
```
$('.list-item').click(function () {
  $('.photo').hide();
});
```

如上写法在每次点击时都会查询 `'.photo'`。推荐写法
```
var $photo;
$('.list-item').click(function () {
  $photo = $photo || $('.photo');
  $photo.hide();
});
```

## 给窗口绑定滚动事件
滚动事件会在滚动时被很频繁的触发，基于性能考虑，要做下节流操作。写法：
```
var scrollTimeout;  // global for any pending scrollTimeout
$(window).scroll(function () {
  if (scrollTimeout) {
    // clear the timeout, if one is pending
    clearTimeout(scrollTimeout);
    scrollTimeout = null;
  }
  scrollTimeout = setTimeout(scrollHandler, 250);
});
scrollHandler = function () {
  // Check your page position and then
  // Load in more results
  // outerPane.html();
};
```

对于 keyup 事件，也可以做如上的处理。

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

推荐阅读： [jQuery Anti-Patterns for Performance](https://www.paulirish.com/2009/perf/)

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d