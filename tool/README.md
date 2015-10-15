# 工具箱

[HTMLelement.info](http://htmlelement.info/)

[Can I use](http://caniuse.com/)

[垂直居中](http://howtocenterincss.com/)

[Mastering the :nth-child](http://nthmaster.com/)

[Regulex](https://jex.im/regulex)

[YOU MIGHT NOT NEED JQUERY](http://youmightnotneedjquery.com/)

[CSS选择器的浏览器支持](http://labs.qianduan.net/css-selector/ "CSS选择器的浏览器支持")

待续...

---
大招：

*  CSS 命名书写顺序,[详情点击](https://www.mozilla.org/css/base/content.css)
	-   display
	- 	list-style
	- 	position
	- 	float
	- 	clear
	- 	width
	- 	height
	- 	margin
	- 	padding
	- 	border
	- 	background
	- 	color
	- 	font
	- 	text-decoration
	- 	text-align
	- 	vertical-align
	- 	white-space
	- 	other text
	- 	content
	 

*  CSS命名规则
   
|	场景 	|	命名 	|	场景 	|	命名 	|
|	  --  	|	  --  	|	  --  	|	  --  	|
|	外层容器 	|	wrap wrapper container 	|	吊顶 	|	top-nav top-bar topbar 	|
|	页头 	|	header 	|	页尾 	|	footer 	|
|	菜单 	|	menu main-menu sub-menu side-nav side-menu 	|	搜索 	|	search search-input search-btn search-results query	|
|	页面主体 	|	content main article 	|	侧边栏 	|	side  sidebar aside 	|
|	LOGO 	|	logo 	|	友情链接 	|	friendlink 	|
|	导航 	|	nav main-nav sub-nav 	|	面包屑 	|	breadcrumb curmb 	|
|	栏目模块 	|	section column module mod 	|	列表 	|	list  news-list pic-list text-list 	|
|	品牌商标 	|	brand branding branding-logo 	|	产品 	|	products products-price products-desc products-review 	|
|	注册 	|	reg register register-box 	|	选项卡 	|	tabs tab news-tab	|
|	评论 	|	review comments 	|	新品 	|	new-release new-products	|
|	生产商 	|	publisher provider 	|	焦点图 	|	focus gallery	|
|	排行榜 	|	rank rank-list 	|	新闻 	|	news info 	|
|	图标 	|	icon ico 	|	头条 	|	top-news headline-news 	|
|	提示技巧 	|	tips note 	|	标题 	|	column-title mod-title 	|
|	登录条 	|	loginbar 	|	指南 	|	guide 	|
|	摘要 	|	summary 	|	投票 	|	vote 	|
|	状态 	|	status 	|	按钮 	|	btn 	|
|	常见问题 	|	faqs 	|	热点 	|	hot 	|
|	当前的 	|	cur current now 	|	标签 	|	tags  tag 	|
|	广告 	|	banner ad-space 	|	提示信息 	|	message msg 	|
|	合作伙伴 	|	partner 	|	链接 	|	link 	|

* IE CSS Hack
 * 内部 Hack  
 ![](https://bradenhan.gitbooks.io/front-end/content/img/CSS-hack1.png)  

 * 选择器 Hack   
 ![](https://bradenhan.gitbooks.io/front-end/content/img/CSS-hack2.png)
	IE10 Hack 可以使用一些 CSS3 来实现，例如 transform。

* 常用 CSS 样式 
  
	1. 绝对定位居中（需固定尺寸）：margin-top 和 margin-left 分别是高宽的一半
		```
		position: absolute; width: 280px; height: 200px;left: 50%; top: 50%; margin: -100px 0 0 -140px

		```
	1.   任意尺寸图片垂直居中：font-size 为容器高度*0.873 
		```
		a {display: table-cell; width:150px; height:100px; vertical-align: middle; *display: block; *font-size:87px;*font-family: Arial;}
		img { vertical-align: middle;} 

		```
	1.   透明度 
	    ```
		opacity: 0.5;filter: alpha(opacity=50);

		```
	1.   水平方向的线性渐变 
		```
		-webkit-linear-gradient(left, #0080ff,#004080); 
		-moz-linear-gradient(left, #0080ff,#004080); 
		-o-linear-gradient(left, #0080ff,#004080); 
		linear-gradient(left, #0080ff,#004080); 
		filter: progid: DXImageTransform.Microsoft.gradient(startcolorstr=#ff0080ff,endcolorstr=#ff004080,gradientType=1)  
		```
	1.   垂直方向的线性渐变
		```
		-webkit-linear-gradient(#0080ff,#004080); 
		-moz-linear-gradient(#0080ff,#004080); 
		-o-linear-gradient(#0080ff,#004080); 
		linear-gradient(#0080ff,#004080); 
		filter: progid: DXImageTransform.Microsoft.gradient(startcolorstr=#ff0080ff,endcolorstr=#ff004080,gradientType=0) 

		```
	1.   Alpha 透明背景色
		```
		background: rgba(0,0,0,.5); 
		filter: progid: DXImageTransform.Microsoft.gradient(startcolorstr=#8000 0000,endcolorstr=#80000000,gradientType=1); 
		需要添加 IE9 hack 以清除 filter 设置： 
		:root selector { filter: none; }  
		```
	1.   利用边框绘制三角形
		```
		width: 0; height: 0; overflow: hidden; border: 10px solid #fff; border-left:10px solid #f00; font: 0/0 arial;

		```
	1.   使用 IE 滤镜的盒阴影
		```
		使用了一个类名为 shadow 的空标签来渲染阴影，而使用一个类名为 container 的标签作为内容容器。在支持 CSS3 盒阴影的浏览器中，使用background: rgba(0,0,0,0)透明 RGBA 颜色来隐藏模拟的阴影。
		HTML： 
			<div> 
				<div class=”shadow”></div> 
					<div class=”container”> 
				</div> 
			</div> 
		CSS： 
		.box {position: relative; width: 400px; height: 300px;} .container {position: absolute; width: 100%; height: 100%; left: 0; top: 0; background: #fff; border: 1px solid #000;} .shadow {position: absolute; width: 100%; height: 100%; left: 3px; top: 3px; background: #000; background: rgba(255,0,0,0); filter: progid: DXImageTransform.Microsoft.blur(makeshadow="1",pixelrad ius=2,shadowopacity=0.35);}  
		```
	1.   用于 IE 滤镜的#AARRGGBB 颜色的透明度速查表
	
| DEC | 0.05 | 0.1 | 0.15 | 0.2 | 0.25 | 0.3 | 0.35 | 0.4 | 0.45 | 0.5  | 
| -- | -- | --| -- | -- | -- | -- | -- | -- | -- | --  |  
| HEX | 0D | 1A | 26 | 33 | 40 | 4D | 59 | 66 | 73 | 7F 
| DEC | 0.55 | 0.6 | 0.65 | 0.7 | 0.75 | 0.8 | 0.85 | 0.9 | 0.95 | 1  | 
| HEX | 8C | 99 | A6 | B3 | BF | CC | D9 | E6 | F2 | FF  |   
	
   * 常用 CSS3 样式(webkit)
  
	1. 渐变（采用兼容老版本 Chrome/Safari 的格式） 
		```
		-webkit-gradient(linear, 0 0, 0 100%, from(#9be), to(#369)); 
		-webkit-gradient(linear, 0 0, 100% 0, from(#9be), to(#369)); 
		-webkit-gradient(linear, 0 0, 0 100%, from(#9be), to(#369), color-stop(0.5,#69b), color-stop(0.5,#69b)); 
		```
	1. 盒阴影（Android 4.0 时不能有-webkit-前缀，而 4.0 以下必须有） 
		```
		-webkit-box-shadow: 1px 1px 3px #000;  box-shadow: 1px 1px 3px #000；
		-webkit-box-shadow: 0 2px 4px rgba(0,0,0,0.4) inset;  box-shadow: 0 2px 4px rgba(0,0,0,0.4) inset； 
		```
	1. 文字阴影（不能有-webkit-前缀） 
		```
		text-shadow: 1px 1px 3px #000 
		```
	1. 圆角（Android 4.0 时不能有-webkit-前缀，而 4.0 以下必须有） 
		```
		-webkit-border-radius: 5px;  border-radius: 5px 
		-webkit-border-bottom-left-radius: 5px;  border-bottom-left-radius: 5px 
		```
	1. 图形边框 
		```
		-webkit-border-image: url(button.png) 0 5 0 5； 
		```
	1. 变形和旋转 
		```
		-webkit-transform: rotate(90deg) skew(30deg, 60deg)
	``` 

