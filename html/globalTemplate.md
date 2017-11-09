# 通用模板 -- 必读大招

### HTML模板

html模板如** 无特殊需求，都需要采用html5声明 **，即 ```<!DOCTYPE html>```，并且需要加上** 兼容的标签 **，以便给客户更好的体验。

+ ** PC端模板 **  

  PC端专题，都需要在专题系统中实现，由于系统原因，暂时只支持gbk编码：

  ** 专题模板 **
```
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
        <meta charset="gb2312"/>
        <title>页面标题</title>
        <style>
            body,div,form,img,p,h1,h2,dl,dt,dd,ul,li{padding:0;margin:0;}
            ul,li{list-style:none;}
            h3,h4,h5{margin: 0;}
            em{font-style:normal;}
            img{display:block;border:0;}
            a{color:#333;text-decoration:none;}
            a:hover,td a:hover{color:#f60;text-decoration:none;}
            .hong12{color:#fff;}
            .clear{clear:both;display:block;height:0;visibility:hidden;font:0/0 arial;}
            .clearfix:after{content:".";display:block;visibility:hidden;clear:both;height:0;font-size:0;}
            .clearfix{*zoom:1;}
            .d-clear{clear:both}
            .d-clear:after{content: ".";display: block;visibility: hidden;clear: both;height: 0;}
            .d-float-left{float: left;}
            #top{font-size:12px;}
        </style>
    </head>
    <body>
	    <div id="top">
            模块内容
        </div>
        <script type="text/javascript">
        </script>   
    </body>
</html> 
```
频道部分，由于历史原因，分为gbk和utf8两种编码，两种编码的不同模板分别如下：

  - ** gbk模板 ** 
  ``` 
  <!DOCTYPE html>
	<html lang="zh-CN">
	    <head>
	        <meta charset="gbk"/>
	        <meta name="renderer" content="webkit"/>
	        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
	        <title>页面标题</title>
	        <meta name="description" content=""/>
	        <meta name="keywords" content=""/>
	        <link rel="stylesheet" href=""/>
	    </head>
	    <body>
	    </body>
	</html>
	```
 
  - ** uft-8模板 **
  ``` 
  <!DOCTYPE html>
	<html lang="zh-CN">
	    <head>
	        <meta charset="utf-8"/>
	        <meta name="renderer" content="webkit"/>
	        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
	        <title>页面标题</title>
	        <meta name="description" content=""/>
	        <meta name="keywords" content=""/>
	        <link rel="stylesheet" href=""/>
	    </head>
	    <body>
	    </body>
	</html>
	```
+ ** 移动端模板 **
	- ** 暂时通用模板 ** 
 
	 ``` 
  	 <!DOCTYPE html>
		<html lang="zh-CN">
	    <head>
	        <meta charset="UTF-8"/>
	        <meta name="HandheldFriendly" content="true" />
	        <meta name="MobileOptimized" content="width" />
	        <meta name="applicable-device" content="mobile"/>
	        <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" />
	        <meta name="keywords" content="" />
	        <meta name="description" content="" />
	        <!-- 取消iphone 和 andirod 手机默认对页面的信息自动识别功能 -->
	        <!-- 电话号码 -->
	        <meta name="format-detection" content="telephone=no" />
	        <!-- 地址 -->
	        <meta name="format-detection" content="address=no" />
	        <!-- 电子邮箱 -->
	        <meta content="email=no" name="format-detection" />
	        <title>
	        </title>
	    </head>
	    <body>
	    </body>
	</html>
  	```
	- ** wap站模板 ** 
	
	如果不使用REM的话，请参考后章：[移动端适配](../mobile/adaptation.html)，否则，请参考上面 ** 通用模板 **。
	- ** H5专题模板 **
	```
	<!doctype html>
<html>
    <head>
        <meta name="apple-touch-fullscreen" content="yes"/>
        <meta name="format-detection" content="telephone=no"/>
        <meta name="apple-mobile-web-app-capable" content="yes"/>
        <meta name="apple-mobile-web-app-status-bar-style" content="black"/>
        <meta HTTP-EQUIV="Pragma" CONTENT="no-cache"/>
        <meta HTTP-EQUIV="Expires" CONTENT="-1"/>
        <title>标题</title>
        <link href="http://atools.fengniao.com/css/rand/17/swiper3.1.0.min.css" type="text/css"/>
        <link rel="stylesheet" type="text/css" href="自己样式"/>
        <script src="http://atools.fengniao.com/js/rand/42/swiper3.1.0.min.js" type="text/javascript">
        </script>
        <script src="自己的脚本">
        </script>
    </head>
    <body>
        <img src="相应src地址" style="width:0;height:0;overflow: hidden;"/> //分享到朋友圈的分享图
        <script type="text/javascript">
		    var w = document.body.offsetWidth;
		    var h = document.body.offsetHeight;
		    if (/Android (\d+\.\d+)/.test(navigator.userAgent)) {
		        var version = parseFloat(RegExp.$1);
		        if (version > 2.3) {
		            var phoneScale = parseInt(window.screen.width) / 640;
		            document.write('<meta name="viewport" content="width=640, minimum-scale = ' + phoneScale + ', maximum-scale = ' + phoneScale + ', target-densitydpi=device-dpi">');
		        } else {
		            document.write('<meta name="viewport" content="width=640, target-densitydpi=device-dpi">');
		        }
		    } else {
		        if (h > 1545) {
		            document.write('<meta name="viewport" content="width=640, user-scalable=yes,minimum-scale =0.5,maximum-scale=2.0,target-      densitydpi=device-dpi">');
		        }
		        else {
		            document.write('<meta name="viewport" content="width=640, user-scalable=yes,minimum-scale =0.5,maximum-scale=0.5,target-densitydpi=device-dpi">');
		        }
		    }
		</script>
    </body>
</html>

	```

+ ** 页面模块 **

  页面模块模板，请参考，本章的第三小节：[模块化](structure.html)