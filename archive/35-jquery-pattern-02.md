# jQuery 模式中篇 前端早读课第35期
 

> There are only two hard things in Computer Science: cache invalidation and naming things.-- Phil Karlton 

## 选择器优化
1， 指定性强的选择器写右边，指定性弱的在写左边。  
jQuery 解析选择器是从右向左解析的。对于选择器 `div a`，jQuery 会先去找所有的 a 标签，然后找 a 标签的祖先元素中有 div 标签的元素。

指定性强的选择器写在右边相比放在左边，能减少查询元素的数量，性能更好。
```
$('div.data .brad')
```

应该优化成
```
$('.data td.brad')
```

2，用更精确的选择器
能用 id 选择器的就用 id 选择器。用 id 选择器找元素比 类选择器快。

```
$('#container div.robotarm');
```

可以优化成

```
 $('#container').find('div.robotarm')
```

3，通配符的优化  
用通配符的查询性能相对比较差。
```
$('.buttons > *')
$('.gender *:radio')
```

可以优化为
```
$('.buttons').children()
$('.gender input:radio')
```

4，不要过分的指定选择器  
过分指定优化器，增加不必要的查询次数，降低性能。
```
$('.data table.attendees td.brad')
```

可以优化为
```
$('.data td.brad')
```

## 用 jQuery 实现发布订阅框架的几种方法
发布/订阅框架用来做对象间做的消息交互，可以降级代码的耦合度。

方法1: 用 `on` 和 `off`   
在 jQuery 中，可以用 `on` 监听自定义事件。用 `off` 来取消监听自定义事件。用 `trigger` 来触发自定义事件。实现如下
```
/* jQuery Tiny Pub/Sub - v0.7 - 10/27/2011
 * http://benalman.com/
 * Copyright (c) 2011 "Cowboy" Ben Alman; Licensed MIT, GPL */
(function($) {
  var o = $({});
  // 订阅事件
  $.subscribe = function() {
    o.on.apply(o, arguments);
  };
  // 取消订阅事件
  $.unsubscribe = function() {
    o.off.apply(o, arguments);
  };
  // 发布事件
  $.publish = function() {
    o.trigger.apply(o, arguments);
  };
}(jQuery));
```

用法
```
function handle(e, a, b, c) {
  // `e` is the event object, you probably don't care about it.
  console.log(a + b + c);
};
$.subscribe("/some/topic", handle);
$.publish("/some/topic", [ "a", "b", "c" ]);
// logs: abc
$.unsubscribe("/some/topic", handle); 
```

方法2：用 `Callbacks`  
调用 `jQuery.Callbacks()` 返回的对象有方法 add, remove 和 fire，对应添加，删除，触发回调函数的功能。实现代码如下
```
var topics = {};
jQuery.Topic = function( id ) {
    var callbacks,
        topic = id && topics[ id ];
    if ( !topic ) {
        callbacks = jQuery.Callbacks();
        topic = {
            publish: callbacks.fire,
            subscribe: callbacks.add,
            unsubscribe: callbacks.remove
        };
        if ( id ) {
            topics[ id ] = topic;
        }
    }
    return topic;
}
```

用法
```
function fn1( value ){
  console.log( value );
}
function fn2( value ){
  fn1("fn2 says:" + value);
  return false;
}
// Usage:
// Subscribers
$.Topic( 'mailArrived' ).subscribe( fn1 );
$.Topic( 'mailArrived' ).subscribe( fn2 );
$.Topic( 'mailSent' ).subscribe( fn1 );
// Publisher
$.Topic( 'mailArrived' ).publish( 'hello world!' );
$.Topic( 'mailSent' ).publish( 'woo! mail!' );
```

方法3: 用 jQuery UI 的 `Observable`  
`$.Observable(观察对象)` 中的观察对象的内容发生改变时，会触发 change 事件。示例如下
```
var myData = [], 
    observer = $.observer(myData);
function dataChange( data ){
   console.log('New data arrived with ID ' + data[0].id + ' and value ' + data[0].title);   
}
$(observer).bind("change", function ( e ) { 
    dataChange( e.target.data );
});
$.observable( myData ).insert({
                id: myData.length + 1,
                title: 'test'
            });
```

该方法不算实现了发布订阅模式。


方法4: 用第三方插件
这种方式就不细讲了，对细节感兴趣的的可以点[这里](https://github.com/shichuan/javascript-patterns/blob/master/jquery-patterns/pubsub-plugin.html)。


所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d