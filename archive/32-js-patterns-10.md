# JavaScript 模式之 parseInt 一定要设置要第二个参数 前端早读课第32期
![](http://upload-images.jianshu.io/upload_images/7219342-6dc4b3557263a58d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 德高望重的大师 Qc Na 曾经和他的学生 Anton 一起散步。Anton 希望引导大师到一个讨论里，说到：大师，我曾听说对象是一个非常好的东西，是这样么？Qc Na 同情地看着他的学生回答到, “愚笨的弟子，对象只不过是可怜人的闭包”
> 
> 被批评后，Anton 离开他的导师并回到了自己的住处，致力于学习闭包。他认真的阅读整个“匿名函数：终极……”系列论文和它的姐妹篇，并且实践了一个基于闭包系统的小的 Scheme 解析器。他学了很多，盼望展现给他导师他的进步。
> 
> 当他下一次与 Qc Na 一同散步时，Anton 试着提醒他的导师，说到 “导师，我已经勤奋地学习了这件事，我现在明白了对象真的是可怜人的闭包。” ，Qc Na 用棍子戳了戳 Anton 回应到，“你什么时候才能学会，闭包才是可怜人的对象”。在那一刻， Anton 明白了什么。
> 
> Anton van Straaten 6/4/2003

## parseInt 设置要第二个参数
如果用 parseInt 将字符串转化成数字，要设置第二个参数为 10。如果不设置第二个参数，以 `0` 打头的数字会认为是八进制的数，如
```
parseInt('09') // 我的Chrome（版本 60） 返回 9。有些浏览器会认为 09 是八进制的数，但 8进制数中不包含数字9，所以最终的结果是0。
parseInt('09', 10) // 这样写就不会出问题。
```

字符串转化数字的其他写法
```
+"08"
Number("08")
"08" - 0
```

所有 JavaScript 模式：http://shichuan.github.io/javascript-patterns/

## 文章推荐
## 《纯前端实现人脸识别-提取-合成》
### 概要
* 用[trackingjs](https://trackingjs.com/) 来识别人脸。
* 用 [AlloyImage](http://alloyteam.github.io/AlloyImage/)(堪称前端PS的前端图像处理类库)，来做图像处理。

阅读地址：http://refined-x.com/2017/09/06/%E7%BA%AF%E5%89%8D%E7%AB%AF%E5%AE%9E%E7%8E%B0%E4%BA%BA%E8%84%B8%E8%AF%86%E5%88%AB-%E6%8F%90%E5%8F%96-%E5%90%88%E6%88%90/


往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d
