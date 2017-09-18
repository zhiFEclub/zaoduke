# 如何看待百度要求内部全面停止使用 React / React Native 早读课第37期
![](http://upload-images.jianshu.io/upload_images/7219342-1fd006f580fa56cd.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

> 我们真的对力量一无所知。 

## 《如何看待百度要求内部全面停止使用 React / React Native》
### 背景
据悉，百度已经要求外部产品线停止使用 React / React Native 等 Facebook 下涉及特定专利条款的开源产品，给半年时间来「转型」，推荐使用 Vue 或者自研的 San 作为替代方案。内部产品如果是新产品，则不能使用 React。

另外百度内部在自研 React Native 的替代方案。

### 概要
* 如果你用了 Facebook 中带 PATENTS License 的开源项目，如 React，可能被 Facebook 告你专利侵权。只要你在用 React，Facebook 侵权你的专利，你也不能告他。而且不只是跟前端相关的专利，而是包括了你拥有的所有专利。
* facebook org 下包含该 PATENTS License 的仓库一共有 107 个。其中涵盖 IOS、Android、PHP、js、Java 等诸多领域 框架/库。（免责声明：筛选结果可能因为关键字不够准确存在偏差）。
前端框架包括： React,React Native,regenerator(babel 有用这个 polyfill generator。这是否意味着 babel 都不能用了？)等。

阅读地址：https://www.zhihu.com/question/65437198/answer/231627090

估计 [preact](https://preactjs.com/)(完全开源版的 React) 要火~ 一堆程序员要加班了。。。

往期前端早读课地址：http://www.jianshu.com/c/0fda3d387a6d