# 通用约定

- 为了避免CSS由于** 编码问题出现中文乱码导致页面解析错误**，CSS中尽量不要出现中文，尤其是属性名，需要的话可以用英文代替，或者转码。
- [字体英文和中文编码对应地址](http://www.jb51.net/css/67658.html 字体英文和中文编码对应地址) 

#### 代码组织
- 以组件为单位组织代码段；
- 制定一致的注释规范，可参考前面 ** [基本原则](https://bradenhan.gitbooks.io/front-end/content/basic/index.html "基本原则") 下面的 统一注释 中关于css注释部分 **；
- `组件块和子组件块`以及`声明块`之间使用**一空行**分隔 ** 注意不要留有多余的空格和空行 **；
- 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动；
- 每个模块之间，需要加上注释，注释名称为模块第一级样式名 

提示：通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。

```css
/**  
 * @Description: the stylesheet section  
 * @authors: XXX (XXX@fengniao.com)
 * @date:    2015-10-12 10:57:15
 * @version: 1.0
 */

```

```
/* section */
.section{padding: 15px; margin-bottom: 15px;}

/* selector */
.section .selector {padding: 15px; margin-bottom: 15px;} 

/* selector-secondary */
.section .selector-secondary {display: block; /* 注释*/}

.section .selector-three {display: span;}
```

#### Class 和 ID
- 使用语义化、通用的命名方式；
- 使用连字符（中划线）- 作为 Class 名称界定符，ID则使用 ** 驼峰命名法或下划线 **；
- 避免选择器嵌套层级过多，尽量少于 3 级；
- 避免选择器和 Class、ID 叠加使用；
- 切片中不应该出现ID，除非有js操作。

出于[性能考量](http://www.stevesouders.com/blog/2009/06/18/simplifying-css-selectors/)，在没有必要的情况下避免元素选择器叠加 Class、ID  使用。

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

#### 声明块格式
- 选择器分组时，保持独立的选择器占用一行；
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
- 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`；

```css
/*  Not recommended  */
.selector, .selector-secondary, .selector[type=text] {padding:15px; margin:0px 0px 15px; background-color:rgba(0, 0, 0, 0.5); box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF}

/* Recommended */
.selector,
.selector-secondary,
.selector[type="text"]{padding: 15px; margin-bottom: 15px; background-color: rgba(0,0,0,.5); box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;}
```

#### 声明顺序
相关属性应为一组，推荐的样式编写顺序: ** 显示属性（position） > 自身属性(box model) > 文本属性(Typographic、Visual) ** 
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

#### 不要使用 `@import`
与 `<link>` 相比，`@import` 要慢很多，不光增加额外的请求数，还会导致不可预料的问题。

替代办法：
- 使用多个 <link> 元素；
- 通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件；
- 其他 CSS 文件合并工具；

参考 [don’t use @import](http://www.stevesouders.com/blog/2009/04/09/dont-use-import/)；

#### 链接的样式顺序：
`a:link -> a:visited -> a:hover -> a:active（LoVeHAte）`

#### CSS3 属性需加浏览器厂商前缀

对于CSS3 属性，需添加浏览器厂商前缀,H5页面，必须要加上谷歌浏览器前缀（-webkit）。

<!-- #### 无需添加浏览器厂商前缀 
使用 [Autoprefixer](https://github.com/postcss/autoprefixer) 自动添加浏览器厂商前缀，编写 CSS 时不需要添加浏览器前缀，直接使用标准的 CSS 编写。

Autoprefixer 通过 [Can I use](http://caniuse.com/)，按兼容的要求，对相应的 CSS 代码添加浏览器厂商前缀。-->
