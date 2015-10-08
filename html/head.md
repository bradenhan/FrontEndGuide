# HEAD

#### 文档类型
为每个 HTML 页面的第一行添加标准模式（standard mode）的HTML5声明， 这样能够确保在每个浏览器中拥有一致的表现。

```html
<!DOCTYPE html>
```

#### 语言属性
为什么使用 lang="zh-cmn-Hans" 而不是我们通常写的 lang="zh-CN" 呢? 请参考知乎上的讨论: [网页头部的声明应该是用 lang="zh" 还是 lang="zh-cn"？](http://www.zhihu.com/question/20797118)

```html
<!-- 中文 -->
<html lang="zh-Hans">

<!-- 简体中文 -->
<html lang="zh-cmn-Hans">

<!-- 繁体中文 -->
<html lang="zh-cmn-Hant">

<!-- English -->
<html lang="en">
```

#### 字符编码
* 以无 BOM 的 utf-8 编码作为文件格式;
* 指定字符编码的 meta 必须是 head 的第一个直接子元素；请参考前端观察的博文： [HTML5 Charset 能用吗？](http://www.qianduan.net/html5-charset-can-it.html)
* 如果资讯、论坛等一些频道，由于`历史原因`需要用 **gbk** 的编码。

```html
<html>
  <head>
    <meta charset="utf-8">
    ......
  </head>
  <body>
    ......
  </body>
</html>
```
```html
<html>
  <head>
    <meta charset="gbk">
    ......
  </head>
  <body>
    ......
  </body>
</html>
```

#### IE 兼容模式
优先使用最新版本的IE 和 Chrome 内核

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
```

#### 360浏览器
由于360浏览器默认模式为IE7模式，为了避免一些错误，需要加上单独的meta标签如下：

```html
<meta name="renderer" content="webkit">
```

#### SEO 优化
```html
<head>
    <meta charset="utf-8">
	<meta name="renderer" content="webkit">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <!-- SEO -->
    <title>Style Guide</title>
    <meta name="keywords" content="your keywords">
    <meta name="description" content="your description"> 
</head>
```

**** 
###以下部分是H5页面需要用到的部分内容

#### viewport
* `viewport`: 一般指的是浏览器窗口内容区的大小，不包含工具条、选项卡等内容；
* `width`: 浏览器宽度，输出设备中的页面可见区域宽度；
* `device-width`: 设备分辨率宽度，输出设备的屏幕可见宽度；
* `initial-scale`: 初始缩放比例；
* `maximum-scale`: 最大缩放比例；

为移动端设备优化，设置可见区域的宽度和初始缩放比例。
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### iOS 图标
* apple-touch-icon 图片自动处理成圆角和高光等效果;
* apple-touch-icon-precomposed 禁止系统自动添加效果，直接显示设计原图;


```html
<!-- iPhone 和 iTouch，默认 57x57 像素，必须有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

<!-- iPad，72x72 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-72x72-precomposed.png" sizes="72x72">

<!-- Retina iPhone 和 Retina iTouch，114x114 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-114x114-precomposed.png" sizes="114x114">

<!-- Retina iPad，144x144 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-144x144-precomposed.png" sizes="144x144">
```

#### favicon
在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 favicon.ico 。为了保证 favicon 可访问，避免404，必须遵循以下两种方法之一：
* 在 Web Server 根目录放置 favicon.ico 文件；
* 使用 link 指定 favicon；

```html
<link rel="shortcut icon" href="path/to/favicon.ico">
```

#### HEAD 模板
```html
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
<head>
    <meta charset="utf-8">
	<meta name="renderer" content="webkit">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <title>Style Guide</title>
    <meta name="description" content="不超过150个字符">
    <meta name="keywords" content=""> 

    <!-- 为移动设备添加 viewport -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- iOS 图标 -->
    <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

    <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml" />
    <link rel="shortcut icon" href="path/to/favicon.ico">
</head>
```
