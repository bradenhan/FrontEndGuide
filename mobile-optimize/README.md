# 移动端优化

#### 通用规则
* WAP/WAP 1.1 
由于许多手机浏览器不支持 CSS、背景图片，所以需要保证为 WAP 开发的网页在没有 CSS 的情况下的可用性。 
许多浏览器（包括 MTK 手机）也不支持 card、go 等 WML 标签，多数情况下应采用 HTML 的格式。 
* WAP 2.0 
WAP 2.0 Profile 是 XHTML1.1 版本，适用大部分 XHTML 规范。为 WAP 2.0 Profile 编写网页时请遵守前面为 PC Web 定义的规范。
* Viewport（webkit） 
在 head 标签内添加 viewport 的 meta 来定义 viewport 大小、是否允许缩放等： 
`<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" /> `
* HTML（webkit） 
为 Webkit 浏览器编写网页时，请尽量使用 HTML5 来实现。 
不可使用 frameset/iframe；不可使用	`<input type="file" />`；合理利用 placeholder 等特有功能；合理利用 video/canvas 等新标签。 
* 图片 --- 双倍图片
由于 Android 1.6 和 iOS 5 能够使用多种屏幕像素密度来表现图像，因此在移动客户端设备的的图片需要考虑至少两种的 DPI 对图片的影响。 
举例来说，iPhone 4 的屏幕分辨率是 640x960，但是在显示网页或应用时，是使用 4 个物理像素来显示一个点，以此达到精致细腻的卓越显示效果。实际上我们需要提供的是 320 像素的内容。  
在此时显示一张 100x75 的图片，由于实际渲染了 200x150 的屏幕区域，而所有硬件图形处理器都会使用简单的线性过渡而不是临近像素的方案来放大图片，因此我们会发现图片在网页中看起来模糊，不够细腻。 
为了达到细腻的效果，我们需要提供一张 200x150 的图片，然后定义它的尺寸为	100x75，例如 
`<img src=”images/product-200x150.png” alt=”” /> `
在背景中使用此种方式时，可以使用 background-size: 100px 75px 来定义背景图片的大小。  
使用 CSS3 和内容生成技术来代替常用的按钮、旗帜、箭头、图标，这样可以不用考虑高 DPI 引起的图像模糊问题，并能提高页面载入性能，减少用户付费流量消耗。 
以下是一些简单的实例：   
关于如何使用 CSS3 和内容生成技术，请参考： [http://nicolasgallagher.com/pure-css-gui-icons/](http://nicolasgallagher.com/pure-css-gui-icons/)  
为简单网页中的像素图片、尺寸极小的图片使用 BASE64 方式载入可以减少 HTTP 请求，节约无线网络连接。因为创建无线网络连接需要消耗大量的时间。 
下面是 BASE64 图片的使用示例： 
`<img src=”data:image/png;base64,iVBOw0ABh...” /> `
.entity { background: url(data:image/png;base64,iVBOw0ABh...) x-repeat 0 0; } 
关于图片转 BASE64 编码请参考：
[http://www.pjhome.net/web/html5/encodeDataUrl.htm](http://www.pjhome.net/web/html5/encodeDataUrl.htm) 

* CSS（webkit） 
不需要添加:hover效果；不需要添加cursor效果；表单对象通常有默认的border-image，如果需要自定义表单对象外观，可以使用样式 border:0 none; border-image:none 来去除 border-image 的影响；或者使用-webkit-appearance属性更改默认表现样式； 
使用 CSS 无法区分 iPhone 和 Android；如要求特别，可以为高 DPI 的屏幕（如 480*800 的 Android 手机和 iPhone4/S 等）
提供高分辨率的背景图，然后使用-webkit-background-sizing来约束大小； 
Android 手机使用圆角边框画出的圆圈锯齿较为严重，如果要求严格，请考虑使用图片实现； 
Android 的 display: none 和 z-index 存在 BUG，有时你可以触摸到隐藏在后面的 Element；因此，应尽量避免使用 position 样式，特别是不要在表单元素上使用。 
* 脚本组件和框架（webkit） 
由于 Webkit 已经实现了大部分框架功能，同时基本上无须考虑跨浏览器兼容性，所以尽量不要使用 jQueryMobile 等大型框架。
* 新的脚本功能和关键词（webkit） 
自带选择器：document.querySelector/querySelectorAll；复制 DOM 对象：Element.cloneNode；多数常用的 prototype 已被实现，例如 Array.forEach, Array.indexOf, Array.lastIndexof, String.trim, String.trimLeft, String.trimRight等；如果需要调试，可以使用 iOS 设备上 Safari 的调试模式； 
三星手机的浏览器获取 DOM 的 innerHTML 对其中的相对路径处理不一样，在	使用innerHTML作为模版的场景需要特别处理。 

## 其他部分可参考下面部分

#### click 的 300ms 延迟响应

click 的 300ms 延迟是由双击缩放(double tap to zoom)所导致的，由于用户可以进行双击缩放或者双击滚动的操作，当用户一次点击屏幕之后，浏览器并不能立刻判断用户是确实要打开这个链接，还是想要进行双击操作。因此，移动端浏览器就等待 300 毫秒，以判断用户是否再次点击了屏幕。

随着响应式网页逐渐增多，用户使用双击缩放机会减少，这 300ms 的延迟就更不可接受了。浏览器开发商也随之提供相应的解决方案。这些方案在[5 Ways to Prevent the 300ms Click Delay on Mobile Devices](http://www.sitepoint.com/5-ways-prevent-300ms-click-delay-mobile-devices/) 中，被提及的包括「禁用缩放」和「width=device-width」等方案，但这些方案并不完美，需要针对某些版本浏览器，又或仅在 Android 的浏览器上使用。

所以这时候就需要一个更简单通用的解决方案，其中 [FT Labs](http://labs.ft.com/) 专门为解决移动端浏览器 300 毫秒点击延迟问题所开发的一个轻量级的库 [FastClick](https://github.com/ftlabs/fastclick) 就是很好的选择。FastClick 在检测到 touchend 事件的时候，会通过 DOM 自定义事件立即触发一个模拟 click 事件，并把浏览器在 300 毫秒之后真正触发的 click 事件阻止掉。

FastClick 的使用方法非常简单，在 window load 事件之后，在 `<body>` 上调用`FastClick.attach()` 即可。

```javascript
window.addEventListener( "load", function() {
    FastClick.attach( document.body );
}, false );
```

#### 快速回弹滚动
快速回弹滚动在手机浏览器上的发展历史：
1. 早期的时候，移动端的浏览器都不支持非 body 元素的滚动条，所以一般都借助 iScroll;
2. Android 3.0 / iOS 解决了非 body 元素的滚动问题，但滚动条不可见，同时 iOS 上只能通过2个手指进行滚动；
3. Android 4.0 解决了滚动条不可见及增加了快速回弹滚动效果，不过随后这个特性又被移除；
4. iOS从5.0开始解决了滚动条不可见及增加了快速回弹滚动效果

如果想要为某个元素拥有 Native 般的滚动效果，可以这样操作：
```css
.element {
    overflow: auto; /* auto | scroll */
    -webkit-overflow-scrolling: touch;
}
```

除了 iScroll 之外，还有一个更加强大的滚动插件 [Swiper](http://www.idangero.us/swiper/#.VfaVk52qqko)，支持 3D 和内置滚动条等。

#### 设备检测
```javascript
// 这段代码引用自：https://github.com/binnng/device.js

var WIN = window;
var LOC = WIN["location"];
var NA = WIN.navigator;
var UA = NA.userAgent.toLowerCase();

function test(needle) {
  return needle.test(UA);
}

var IsTouch = "ontouchend" in WIN;
var IsAndroid = test(/android|htc/) || /linux/i.test(NA.platform + "");
var IsIPad = !IsAndroid && test(/ipad/);
var IsIPhone = !IsAndroid && test(/ipod|iphone/);
var IsIOS = IsIPad || IsIPhone;
var IsWinPhone = test(/windows phone/);
var IsWebapp = !!NA["standalone"];
var IsXiaoMi = IsAndroid && test(/mi\s+/);
var IsUC = test(/ucbrowser/);
var IsWeixin = test(/micromessenger/);
var IsBaiduBrowser = test(/baidubrowser/);
var IsChrome = !!WIN["chrome"];
var IsBaiduBox = test(/baiduboxapp/);
var IsPC = !IsAndroid && !IsIOS && !IsWinPhone;
var IsHTC = IsAndroid && test(/htc\s+/);
var IsBaiduWallet = test(/baiduwallet/);
```

#### 获取滚动条值
PC 端滚动条的值是通过 `document.scrollTop` 和 `document.scrollLeft` 获得，但在 iOS 中并没有滚动条的概念，所以仅能通过 windows.scroll 获取，同时也能兼容 Android 。
```javascript
window.scrollY
window.scrollX
```

#### 清除输入框内阴影
在 iOS 上，输入框默认有内部阴影，但无法使用 box-shadow 来清除，如果不需要阴影，可以这样操作：
```css
input,
textarea {
    border: 0; /* 方法1 */
    -webkit-appearance: none; /* 方法2 */
}
```

#### Meta 相关
##### 页面窗口自动调整到设备宽度，并禁止用户缩放页面

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no" />
```

##### 电话号码识别

iOS Safari ( Android 或其他浏览器不会) 会自动识别看起来像电话号码的数字，将其处理为电话号码链接，比如：
- 7位数字，形如：1234567
- 带括号及加号的数字，形如：(+86)123456789
- 双连接线的数字，形如：00-00-00111
- 11位数字，形如：13800138000

```html
<!-- 关闭电话号码识别： -->
<meta name="format-detection" content="telephone=no" />

<!-- 开启电话功能： -->
<a href="tel:123456">123456</a>

<!-- 开启短信功能： -->
<a href="sms:123456">123456</a>
```

##### 邮箱地址的识别

在 Android （ iOS 不会）上，浏览器会自动识别看起来像邮箱地址的字符串，不论有你没有加上邮箱链接，当你在这个字符串上长按，会弹出发邮件的提示。
```html
<!-- 关闭邮箱地址识别： -->
<meta name="format-detection" content="email=no" />

<!-- 开启邮件发送： -->
<a mailto:>mobile@gmail.com">mobile@gmail.com</a>
```

##### 指定 iOS 的 safari 顶端状态条的样式

```html
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!-- 可选default、black、black-translucent -->
```
