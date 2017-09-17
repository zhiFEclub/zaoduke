# jQuery 模式下篇 前端早读课第36期
![](http://upload-images.jianshu.io/upload_images/7219342-5733beec92de59ec.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 年少不知愁滋味，为赋新词常说愁。
年少不听李宗盛，听懂已是不惑年。

本期编辑 [小虫巨蟹](http://www.jianshu.com/u/7233332cb959)。

## jQuery 插件写法
最简单的写法如下：
```
$.fn.myPluginName = function() {
    // your plugin logic
}
```

如下写法不会和别的库冲突，推荐：

```
(function( $ ){
    $.fn.myPluginName = function() {
      // your plugin logic
    };
})( jQuery );
```

插件参数和自定义参数的合并，用 `$.extend` ，也可以用 `Object.assign`。
```
;( function( $ ){
  $.fn.extend( {
    pluginname: function( options ) {
      this.defaults = {};
      // 插件参数和自定义参数的合并
      var settings = $.extend( {}, this.defaults, options );
      return this.each( function() {
        var $this = $( this );
      });
    }
  });
})( jQuery );
```

写 jQuery 插件的模板如下：

```
;(function ( $, window, document, undefined ) {
var pluginName = 'defaultPluginName',
    defaults = {
        propertyName: "value"
    };

function Plugin( element, options ) {
    this.element = element;

    this.options = $.extend( {}, defaults, options) ;
    this._defaults = defaults;
    this._name = pluginName;
    this.init();
}
Plugin.prototype.init = function () {
    // 初始化代码
};

$.fn[pluginName] = function ( options ) {
    return this.each(function () {
        if (!$.data(this, 'plugin_' + pluginName)) {
            $.data(this, 'plugin_' + pluginName,
            new Plugin( this, options ));
        }
    });
}
})( jQuery, window, document );
```

组件之间通信，用自定义事件的方式，可以做到很好的代码解耦：
```
;(function ( $, window, document, undefined ) {
    $.widget("ao.eventStatus", {
        options: {
        },
        _create : function() {
            var self = this;
            //self.element.addClass( "my-widget" );
            //subscribe to 'myEventStart'
            self.element.bind( "myEventStart", function( e ) {
                console.log("event start");
            });
            //subscribe to 'myEventEnd'
            self.element.bind( "myEventEnd", function( e ) {
                console.log("event end");
            });
            //unsubscribe to 'myEventStart'
            //self.element.unbind( "myEventStart", function(e){
                ///console.log("unsubscribed to this event");
            //});
        },
        destroy: function(){
            $.Widget.prototype.destroy.apply( this, arguments );
        },
    });
})( jQuery, window , document );
```

让写的 jQuery 的插件既支持 AMD 又支持 CommonJS 的方式见[这里](https://github.com/shichuan/javascript-patterns/tree/master/jquery-plugin-patterns/amd-commonjs)。

## 文章推荐
## 《基于 Node、WebSocket 的手机控制电脑实例》
### 背景
如果不关注底层协议细节，WebSocket 基板上一句话就可以说清楚：WebSocket 是建立在传输层 TCP 之上，并且依赖于 HTTP 的应用层协议，它的出现主要是为了弥补 HTTP 协议中，服务器端无法主动推送消息到客户端的缺陷。但是这样对初学者的帮助远远不够，不如直接有实例来的直观。

### 概要
* 实例介绍、效果预览
* 实现思路
* 代码实现

阅读地址：https://juejin.im/post/59bccffa5188257e764c8216