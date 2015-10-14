# HEAD

#### 文档类型
为每个 HTML 页面的第一行添加标准模式（standard mode）的HTML5声明， 这样能够确保在每个浏览器中拥有一致的表现。

```html
<!DOCTYPE html>
```

#### 语言属性 (酌情采用)
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
#### meta标签
<meta> 元素可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。
<meta> 标签位于文档的头部，不包含任何内容。<meta> 标签的属性定义了与文档相关联的名称/值对。
详细可查看[HTML META 标签](http://www.w3school.com.cn/tags/tag_meta.asp "HTML <meta> 标签")

常用的meta标签如下,[详情可查看](http://fex.baidu.com/blog/2014/10/html-head-tags/ "百度FEX HTML head 头标签")：
```
<meta charset="utf-8">
<meta name="renderer" content="webkit">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<meta name="keywords" content="your keywords">
<meta name="description" content="your description"> 

以下是移动端用的比较多的
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<meta name="format-detection"content="telephone=no, email=no" />
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
<meta name="apple-mobile-web-app-capable" content="yes" /><!-- 删除苹果默认的工具栏和菜单栏 -->
<meta name="apple-mobile-web-app-status-bar-style" content="black" /><!-- 设置苹果工具栏颜色 -->
<meta name="format-detection" content="telphone=no, email=no" /><!-- 忽略页面中的数字识别为电话，忽略email识别 -->
<!-- 启用360浏览器的极速模式(webkit) --> 
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">
<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">
<!-- 适应移动端end -->
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
**H1**标签和**H2**标签为SEO预留，所以，页面上尽量不要有H1和H2标签。

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

#### HEAD 模板 (可根据实际项目斟酌加减meta标签)
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
    <link rel="shortcut icon" href="path/to/favicon.ico">
</head>
```
