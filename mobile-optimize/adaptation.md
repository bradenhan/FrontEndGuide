# 移动端优化  

### 移动端屏幕适配

现在手机屏幕是越来越大，各种分辨率也越来越多。从2010年的iPhone 4，到2015年的iPhone 6 plus，从小米1到现在的小米 note3... 
每年都会有新的手机出现，而且手机屏幕也越来越杂乱。我们的手机网站需要尽量适配更多手机；更有甚者，某些情况下横竖屏切换时都要适配。为了节约成本和时间，移动端适配显得越来越重要。

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
lib-flexible库的使用方法非常的简单，只需要在Web页面的<head></head>中添加对应的flexible_css.js,flexible.js文件：

第一种方法是将文件下载到你的项目中，然后通过相对路径添加: 
```
<script src="build/flexible_css.debug.js"></script>
<script src="build/flexible.debug.js"></script> 
```
或者直接加载阿里CDN的文件：
```
<script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script>
```
**html模板**
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta content="yes" name="apple-mobile-web-app-capable">
        <meta content="yes" name="apple-touch-fullscreen">
        <meta content="telephone=no,email=no" name="format-detection">
        <script src="build/flexible_css.debug.js"></script>
		script src="build/flexible.debug.js"></script>
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




## 参考资料
+ [lib.flexible - 淘宝移动端自适应方案](https://github.com/amfe/lib-flexible)
+ [使用Flexible实现手淘H5页面的终端适配](http://web.jobbole.com/84285/)
+ [viewports剖析](http://www.w3cplus.com/css/viewports.html)
+ [移动端高清、多屏适配方案](http://www.html-js.com/article/Mobile-terminal-H5-mobile-terminal-HD-multi-screen-adaptation-scheme%203041)
+ [移动端屏幕适配viewport](http://www.ituring.com.cn/article/130015)
+ [移动端适配基础(rem,vw,vh)](https://segmentfault.com/a/1190000003101394)
+ [CSS值转REM的Sublime Text插件 - GitHub](https://github.com/flashlizi/cssrem)
  
