# 通用约定

  为了避免CSS由于** 编码问题出现中文乱码导致页面解析错误**，CSS中尽量不要出现中文，尤其是属性名，需要的话可以用英文代替，或者转码。
 [字体英文和中文编码对应地址](http://www.jb51.net/css/67658.html 字体英文和中文编码对应地址) 


####行内、页内和外部样式表
* 行内样式应该只出现在不定尺寸的动态图片上，且仅用来定义高度和宽度来防止图像抖动（通常后端开发人员会使用 width 和 height 属性来做这一点，所以基本上不会出现这样的情况）。

* 页内的样式大部分时候不应该出现，除非有以下情况：
 * 后续的脚本需要根据样式来运行，而又不能绑定在window.onload事件上；
 * 为了防止样式加载不顺利而出现裸奔的重要页面；


* 链接外部样式表有两种方式：使用<link>标签和使用@import。由于不同浏览在载入 CSS 文件时间采用的处理方式不同，易造成载入延迟，切不可混合使用这两种方式。在当前没有进行统一 CSS 文件规划的情况下，我们**统一使用<link>标签来链接外部样式表**。    
** 不要使用 `@import`**
与 `<link>` 相比，`@import` 要慢很多，不光增加额外的请求数，还会导致不可预料的问题。

	** 替代办法** ：
	- 使用多个 <link> 元素；
	- 通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件；
	- 其他 CSS 文件合并工具；
	
	参考 [don’t use @import](http://www.stevesouders.com/blog/2009/04/09/dont-use-import/)；

#### 代码格式
- 以组件为单位组织代码段；
- 制定一致的注释规范，可参考前面 ** [基本原则](https://bradenhan.gitbooks.io/front-end/content/basic/index.html "基本原则") 下面的 统一注释 中关于css注释部分 **；
- `组件块和子组件块`以及`声明块`之间使用**一空行**分隔 ** 注意不要留有多余的空格和空行 **； 
- 每个模块之间，需要加上注释，注释名称为模块第一级样式名;
- 声明块的左括号 `{` 前不需要添加空格；
- 声明块的右括号 `}` 应单独成行；
- 声明语句中的 `:` 后应添加一个空格；
- 声明语句中属性名和属性值之间需要留有一个空格
- 声明语句中属性和属性之间需要留有一个空格 
- 声明语句应以分号 `;` 结尾；
- 一般以逗号分隔的属性值，每个逗号后应添加一个空格；
- `rgb()`、`rgba()`、`hsl()`、`hsla()` 或 `rect()`  括号内的值，逗号分隔，但逗号后不添加一个空格；
- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，`.5` 代替 `0.5`；`-.5px` 代替 `-0.5px`）；
- 十六进制值应该全部小写和尽量简写，例如，`#fff` 代替 `#ffffff`；
- 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`

提示：通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。 

```
/* section */
.section{padding: 15px; margin-bottom: 15px;}

/* selector */
.section .selector {padding: 15px; margin-bottom: 15px;} 

/* selector-secondary */
.section .selector-secondary {display: block; /* 注释*/}

.section .selector-three {display: span;}
```
#### 声明块格式
- 声明CSS文件或者模块

```css
/**  
 * @Description: the stylesheet section  
 * @authors: XXX (XXX@fengniao.com)
 * @date:    2015-10-12 10:57:15
 * @version: 1.0
 */

```
- 选择器分组时，保持独立的选择器占用一行； 
  
```css
/*  Not recommended  */
.selector, .selector-secondary, .selector[type=text] {padding:15px; margin:0px 0px 15px; background-color:rgba(0, 0, 0, 0.5); box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF}

/* Recommended */
.selector,
.selector-secondary,
.selector[type="text"]{padding: 15px; margin-bottom: 15px; background-color: rgba(0,0,0,.5); box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;}
``` 

#### Reset 和清除浮动
页面 reset 代码主要用清除部分标签的默认边距和内边距、定义默认文字样式、添加清除浮动代码等。目前使用的 reset 代码分如下，请酌情使用：
 * ** Reset ** 
 
```
body,h1,h2,h3,h4,h5,h6,dl,dt,dd,ul,ol,li,th,td,p,blockq
uote,pre,form,fieldset,legend,input,button,textarea,hr{margin:0;padding:0;}
ul,ol{list-style:none;}
body{font:12px/1.5 Arial; color:#333}
select,input,button{vertical-align:middle;font-size:100%;}
fieldset,img{border:0 none;}
em{font-style:normal;}
.clear {clear:both;display:block;height:0;
visibility:hidden; font:0/0 Arial}
.clearfix:after {content:"."; display: block; height: 0;
clear: both; visibility: hidden; font-size:0}
.clearfix {*zoom:1}
```
* ** 清除浮动 **
使用类型.clearfix 为有外层容器的模块清除浮动，但不可滥用；
如果一种 CSS 类型都需要清除浮动，可以将此类型添加在.clearfix 后面，而不是为使用这个类型的 HTML 标签都添加.clearfix 类型。
使用类型`<div class="clear"></div>`为没有外层容器的模块清除浮动。

#### 选择器的使用和命名
CSS 选择器是 CSS 重要的组成部分。为了保持最大的浏览器兼容性，我们目前主要能使用的选择器只有：标签选择器， ID 选择器，类选择器，子对象选择器。

* 标签选择器： ** 不允许使用 h1/h2 作为选择器： h1/h2 标签将预留给 SEO **。 
* 类选择器的命名：浏览器目前支持的规则是只能以字母、下划线+字母开始。而我们要求必须以字母开始，以模块的样式特征或功能特征的英文命名。需要多个单词且单词间容易混在一起时，中间使用“ -”连接（输入下划线需要按住 shift 键，不方便）。
* ID选择器命名：使用驼峰命名法命名。
* 名称较长时建议使用缩写，但是必须是通用的、 约定俗成的或一目了然的缩写。 ** `绝不可使用拼音` **。
  **不要使用有歧义的缩写来命名，例如：**
 * 不使用 hd 作为 header 的缩写，因为 hd 最主要的含义是高清
 * 不使用 mod 作为 module 的缩写，因为 mod 的主要用来表示汽车电脑硬件改造和
 * 游戏模型改造，同时它也是计算中求余数的运算符。
建议使用 HTML5 的标签名作为相应功能替代容器的 CSS 类名，例如： header, nav,menu, section, article, aside, canvas, footer 等。 当页面升级到 HTML5 时，这种方式可以更少的修改 HTML 和 CSS 代码。


避免选择器嵌套层级过多，尽量少于 3 级；
使用子选择器时，层次不应超过 3 个。例如 .section article li 是可以的，但是应避免.section article li a 这样的情况。 

出于[性能考量](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/)，避免元素选择器叠加 Class、ID  使用。

元素选择器和 ID、Class 混合使用也违反关注分离原则。如果HTML标签修改了，就要再去修改 CSS 代码，不利于后期维护。


```css
/* Not recommended */
.red {}
.box_green {}
.page .header .login #username input {}
ul#example {}

/* Recommended */
#nav {}
.box-video {}
#username input {}
#example {}
```   
#### 样式声明顺序
相关属性应为一组，推荐的样式编写顺序: ** 显示属性（position） > 自身属性(box model) > 文本属性(Typographic、Visual) ** ，详情可查看本文档的工具箱。

1. Positioning
2. Box model
3. Typographic
4. Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型决定了组件的尺寸和位置，因此排在第二位。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

```css
.declaration-order {
  /* Positioning */
  position: absolute; top: 0; right: 0; bottom: 0; left: 0; z-index: 100;

  /* Box model */
  display: block; box-sizing: border-box; width: 100px; height: 100px; padding: 10px; border: 1px solid #e5e5e5; border-radius: 3px; margin: 10px; float: right; overflow: hidden;

  /* Typographic */
  font: normal 13px "Helvetica Neue", sans-serif; line-height: 1.5; text-align: center;

  /* Visual */
  background-color: #f5f5f5; color: #fff; opacity: .8;

  /* Other */
  cursor: pointer;
}
```
#### 引号使用
`url()` 、属性选择符、属性值使用双引号。
参考 [Is quoting the value of url() really necessary?](http://stackoverflow.com/questions/2168855/is-quoting-the-value-of-url-really-necessary)
```css
/* Not recommended */
@import url(//www.google.com/css/maia.css);

html {
  font-family: 'open sans', arial, sans-serif;
}

/* Recommended */
@import url("//www.google.com/css/maia.css");

html {
  font-family: "open sans", arial, sans-serif;
}

.selector[type="text"] {

}
```

#### 媒体查询（Media query）的位置
将媒体查询放在尽可能放在页面底部。如果页面有压缩，需要检查压缩后的媒体查询语句是否正常【主要是大括号问题】。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

....

@media (max-width: 768px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```   
#### 链接的样式顺序：
`a:link -> a:visited -> a:hover -> a:active（LoVeHAte）`

#### CSS3 属性需加浏览器厂商前缀

对于CSS3 属性，需添加浏览器厂商前缀,H5页面，必须要加上谷歌浏览器前缀（-webkit）。

<!-- #### 无需添加浏览器厂商前缀 
使用 [Autoprefixer](https://github.com/postcss/autoprefixer) 自动添加浏览器厂商前缀，编写 CSS 时不需要添加浏览器前缀，直接使用标准的 CSS 编写。

Autoprefixer 通过 [Can I use](http://caniuse.com/)，按兼容的要求，对相应的 CSS 代码添加浏览器厂商前缀。-->

