# 移动端优化  

### 移动端屏幕适配

现在手机屏幕是越来越大，各种分辨率也越来越多。从2010年的iPhone 4，到2015年的iPhone 6 plus，从小米1到现在的小米 note3... 
每年都会有新的手机出现，而且手机屏幕也越来越杂乱。我们的wap站需要尽量适配更多手机；更有甚者，某些情况下横竖屏切换时都要适配。为了节约成本和时间，移动端适配显得越来越重要。

那么应该如何去做才能实现呢？这是我们需要思考的问题。

移动端适配，暂时分两种情况：

- ** 专题适配** ：
  专题部分，暂时以640为基础，针对不同分辨率做缩放设置，实现代码如下：
  ```
  <script>
	   if (/Android (\d+\.\d+)/.test(navigator.userAgent)) {
	    if (parseFloat(RegExp.$1) > 2.3) {
	     var phoneScale = parseInt(window.screen.width) / 640;
	     document.write('<meta name="viewport" content="width=640, minimum-scale=' + phoneScale + ', maximum-scale=' + phoneScale + ', target-densitydpi=device-dpi" />');
	    } else {
	     document.write('<meta name="viewport" content="width=640, target-densitydpi=device-dpi" />');
	    }
	   } else {
	    document.write('<meta name="viewport" content="width=640,user-scalable=no, target-densitydpi=device-dpi" />');
	   }
   </script>   
  ```	
  用此种方法，实现meta标签（viewport）的动态变化。

- ** wap站适配 ** ：
前端中心暂时以淘宝的[lib-flexible](https://github.com/amfe/lib-flexible)为基础，结合自身的情况，整理了一套解决方案。先暂时试行，以后再慢慢完善。 
 
##如何实现
#### 第一步 ： 新建html模板
lib-flexible库的使用方法非常的简单，只需要在Web页面的<head></head>中添加对应的flexible_css.js,flexible.js文件，需要注意两个文件的书写顺序：

第一种方法是将文件下载到你的项目中，然后通过相对路径添加: 
```
<script src="build/flexible_css.js"></script>
<script src="build/flexible.js"></script> 
```
或者直接加载阿里CDN的文件：
```
<script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script>
```
** 修改后的地址：[flexible.js](flexible.js)、[flexible_css.js](flexible_css.js)，我们需要用这个** 。

**html模板**
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta content="yes" name="apple-mobile-web-app-capable">
        <meta content="yes" name="apple-touch-fullscreen">
        <meta content="telephone=no,email=no" name="format-detection">
        <script src="build/flexible_css.js"></script>
		script src="build/flexible.js"></script>
        <link rel="apple-touch-icon" href="favicon.png">
        <link rel="Shortcut Icon" href="favicon.png" type="image/x-icon">
        <title>再来一波</title>
    </head>
    <body>
        <!-- 页面结构写在这里 -->
    </body>
</html>
```
#### 第二步： 把视觉稿中的px转换成rem

目前Flexible会将视觉稿分成16份，而每一份被称为一个单位rem。针对我们这份视觉稿可以计算出：  
1rem = 640/16=40px

```<html>```对应的font-size为40px：

这样一来，对于视觉稿上的元素尺寸换算，只需要原始的px值除以rem基准值即可。例如此例视觉稿中的图片，其尺寸是100px * 100px,转换成为2.5rem * 2.5rem。

**快速计算方法**
在实际生产当中，如果每一次计算px转换rem，会觉得非常麻烦，直接影响大家的开发效率。为了能让大家更快进行转换，前端这边找了一个小的工具，可以吧px转换rem，写的时候按照像素就好，会直接转换成相应尺寸的rem。

** [cssrem](https://github.com/flashlizi/cssrem)** 是一个CSS的px值转rem值的Sublime Text3自动完成插件。这个插件是由@正霖编写。先来看看插件的效果：

![](CSSREM.gif)

有关于CSSREM如何安装、配置教程可以[点击这里查阅](https://github.com/flashlizi/cssrem)。

还有好多工具，在这里就不一一做介绍了，如果想谅解更多，请问[度娘](https://www.baidu.com/)。 

**字号不使用rem**

前面我们见证了如何使用rem来完成H5适配。那么文本又将如何处理适配。是不是也通过rem来做自动适配。

显然，我们在iPhone3G和iPhone4的Retina屏下面，希望看到的文本字号是相同的。也就是说，我们不希望文本在Retina屏幕下变小，另外，我们希望在大屏手机上看到更多文本，以及，现在绝大多数的字体文件都自带一些点阵尺寸，通常是16px和24px，所以我们不希望出现13px和15px这样的奇葩尺寸。

如此一来，就决定了在制作H5的页面中，rem并不适合用到段落文本上。所以在Flexible整个适配方案中，考虑文本还是使用px作为单位。只不过使用[data-dpr]属性来区分不同dpr下的文本字号大小。 

>  
.selector {
    width: 2rem;
    border: 1px solid #ddd;
}
**[data-dpr="1"]** .selector {
    height: 32px;
    font-size: 14px;
}
**[data-dpr="2"]** .selector {
    height: 64px;
    font-size: 28px;
}
**[data-dpr="3"]** .selector {
    height: 96px;
    font-size: 42px;
} 

其实H5适配的方案有很多种，网上有关于这方面的教程也非常的多。不管哪种方法，都有其自己的优势和劣势。而我们主要介绍的是如何使用Flexible这样的一库来完成H5页面的终端适配。为什么推荐使用Flexible库来做H5页面的终端设备适配呢？主要因为这个库在手淘已经使用了近一年，而且已达到了较为稳定的状态。除此之外，你不需要考虑如何对元素进行折算，可以根据对应的视觉稿，直接切入。 

## 参考资料
+ [lib.flexible - 淘宝移动端自适应方案](https://github.com/amfe/lib-flexible)
+ [使用Flexible实现手淘H5页面的终端适配](http://web.jobbole.com/84285/)
+ [viewports剖析](http://www.w3cplus.com/css/viewports.html)
+ [移动端高清、多屏适配方案](http://www.html-js.com/article/Mobile-terminal-H5-mobile-terminal-HD-multi-screen-adaptation-scheme%203041)
+ [移动端屏幕适配viewport](http://www.ituring.com.cn/article/130015)
+ [移动端适配基础(rem,vw,vh)](https://segmentfault.com/a/1190000003101394)
+ [CSS值转REM的Sublime Text插件 - GitHub](https://github.com/flashlizi/cssrem)
  
