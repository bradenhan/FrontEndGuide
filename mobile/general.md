# 通用规则
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
 
	> 
举例来说，iPhone 4 的屏幕分辨率是 640x960，但是在显示网页或应用时，是使用 4 个物理像素来显示一个点，以此达到精致细腻的卓越显示效果。实际上我们需要提供的是 320 像素的内容。  
在此时显示一张 100x75 的图片，由于实际渲染了 200x150 的屏幕区域，而所有硬件图形处理器都会使用简单的线性过渡而不是临近像素的方案来放大图片，因此我们会发现图片在网页中看起来模糊，不够细腻。 
为了达到细腻的效果，我们需要提供一张 200x150 的图片，然后定义它的尺寸为	100x75，例如`<img src=”images/product-200x150.png” alt=”” /> `
在背景中使用此种方式时，可以使用 background-size: 100px 75px 来定义背景图片的大小。 

   
* 使用 CSS3 和内容生成技术来代替常用的按钮、旗帜、箭头、图标，这样可以不用考虑高 DPI 引起的图像模糊问题，并能提高页面载入性能，减少用户付费流量消耗。 
> 
以下是一些简单的实例：   
关于如何使用 CSS3 和内容生成技术，请参考： [http://nicolasgallagher.com/pure-css-gui-icons/](http://nicolasgallagher.com/pure-css-gui-icons/)  
为简单网页中的像素图片、尺寸极小的图片使用 BASE64 方式载入可以减少 HTTP 请求，节约无线网络连接。因为创建无线网络连接需要消耗大量的时间。 
下面是 BASE64 图片的使用示例： `<img src=”data:image/png;base64,iVBOw0ABh...” /> `
.entity { background: url(data:image/png;base64,iVBOw0ABh...) x-repeat 0 0; } 
关于图片转 BASE64 编码请参考：[http://www.pjhome.net/web/html5/encodeDataUrl.htm](http://www.pjhome.net/web/html5/encodeDataUrl.htm) 
 
* CSS（webkit） 
wap端由于设备等原因影响和PC端有一些区别：
 * 不需要添加:hover效果；
 * 不需要添加cursor效果；
 * 表单对象通常有默认的border-image，如果需要自定义表单对象外观，可以使用样式 border:0 none; border-image:none 来去除border-image 的影响；或者使用-webkit-appearance属性更改默认表现样式；
 * 
使用 CSS 无法区分 iPhone 和 Android；如要求特别，可以为高 DPI 的屏幕（如 480*800 的 Android 手机和 iPhone4/S 等）提供高分辨率的背景图，然后使用-webkit-background-sizing来约束大小； 
 * Android 手机使用圆角边框画出的圆圈锯齿较为严重，如果要求严格，请考虑使用图片实现（此种情况在安卓2.2以下显示明显，现在几乎可以忽略不计）； 
 * Android 的 display: none 和 z-index 存在 BUG，有时你可以触摸到隐藏在后面的 Element；因此，应尽量避免使用 position 样式，特别是不要在表单元素上使用。  
  <br />
* 脚本组件和框架（webkit） 
由于 Webkit 已经实现了大部分框架功能，同时基本上无须考虑跨浏览器兼容性，所以尽量不要使用 jQueryMobile 等大型框架。

* 新的脚本功能和关键词（webkit） 
 * 自带选择器：document.querySelector/querySelectorAll；
 * 复制 DOM 对象：Element.cloneNode；
 * 多数常用的 prototype 已被实现，例如 Array.forEach, Array.indexOf, Array.lastIndexof, String.trim, String.trimLeft, String.trimRight等；
 * 如果需要调试，可以使用 iOS 设备上 Safari 的调试模式； 
 * 三星手机的浏览器获取 DOM 的 innerHTML 对其中的相对路径处理不一样，在	使用innerHTML作为模版的场景需要特别处理。 