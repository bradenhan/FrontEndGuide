# 通用约定

#### 标签
* 自闭合（self-closing）标签，无需闭合，但是还是建议关闭 ( 例如： `img` `input` `br` `hr` 等 )，虽然 HTML5 标准已不再强制， 建议还是关闭所有关闭标签， 使文档可以被识别为 xml，以适用更广的范围;
* 可选的闭合标签（closing tag），必须闭合 ( 例如：`</li>` 或 `</body>` )，如果不闭合，在低版本浏览器下会导致错误；
* 尽量减少标签数量，但是也需要保持一定的 **``可扩展性``**（PC页面嵌套**最好**不要超过12层，H5页面酌情而定）；


```html
<img src="images/google.png" alt="Google">
<input type="text" name="title">

<ul>
  <li>Style</li>
  <li>Guide</li>
</ul>
 
<span class="avatar">
  <img src="...">
</span>
 
<img class="avatar" src="...">  

```

#####标签使用补录 （大招）：
除了标签应具有语义化特征外，还应该在使用上符合以下规范：
* 空标签： 尽量不要有空标签，除非为了网页的特殊效果需要或为了兼容低版本浏览器而不得不这样定义（例如清除浮动、半透明背景等）。
* ** A **： 必须为A添加 href 属性，否则就不应该使用A标签。
* ** IMG：** 必须为`<img>`标签添加 alt 属性。 除非有脚本希望计算图片原始大小，必须为IMG设定高度和宽度（有时可仅设置其中一项）以防止抖动。可以使用 CSS、行内 style、 width/height 属性来设置。
* ** DL DD DT ** ： DL中的DT和DD不需要一一对应，但多数情况下应在它们一一对应时使用，否则可能存在滥用。
* ** FORM** ： 表单对象应包含在FORM标签内，除非页面必须依赖 AJAX 来实现。但是请不要为FORM 定义样式，并且FORM标签不得参与页面布局。
* ** LABEL **： 当表单的输入框、单选框、复选框、多行文本框、下拉选项等有标签文字时，必须将这些文字用LABEL标签包含，并使用 FOR 属性进行连接。
* ** TABLE** ： 当内容是表格形式时，应果断使用table。
可以使用 table 的 border-spacing/ border-collapse 样式、单元格的 padding 样式来取代表格的 cellspacing 和 cellpadding 属性，因此`<table>`上应该只能具有 id、class、 summary 和自定义的属性。
建议为表格添加 summary 属性作为表格的说明，它可被屏幕阅读器识别，也可作为模块识别标志。
完整的table标签如下：
      <table summary="表格的说明">
		<caption>标题</caption>
			<colgroup>
			<col class="name" />
		<col />
		</colgroup>
		<thead>
			<tr>
			<th>名称</th>
			<th>操作</th>
			</tr>
		</thead>
		<tfoot>
			<tr><td colspan="2">第一页</td></tr>
		</tfoot>
		<tbody>
			<tr><td></td><td></td></tr>
			<tr><td></td><td></td></tr>
		</tbody> 
	</table>
合理的利用表格的这些标签将为我们开发提供便利。  
表头应使用th作为单元格标签。

* ** LINK ** ： 链接外部样式表： &lt;link href="css/sky.css"rel="stylesheet" /&gt;， 不再需要类型声明（如果需要，请添加媒体选择属性）；必须放在head标签内。
*  ** STYLE **： 页内样式： style.../style；必须放在head标签内， 不再需要类型声明。
*  ** SCRIPT **： 不应为&lt;script&gt;标签添加 language 属性， 也不再需要为标签定义 type 属性。
 * 链接外部脚本： &lt;script src="js/jquery.js"&gt;&lt;/script&gt;；尽量放在需要使用之前一行。
 * 页内脚本： &lt;script&gt;...&lt;/script&gt;；放置在需要使用处。多数情况下，应位于&lt;/body&gt;前。

#### SEO 和预留
 * SEO 相关
  为搜索引擎优化预留 h1 和 h2 标签：在此类标签上定义 class 来定义样式。

 * 属性预留
   除非表单对象和框架，不得使用 name 属性。
   为 JavaScript 开发和表单对象预留 id 属性：除非所有 JavaScript 由前端组完成，尽量不使用 id 选择器（ #）。

#### Class 与 Id
* class 应以** 功能** 或** 内容** 命名，不以表现形式命名；
* class 与 id 单词字母小写，多个单词组成时，采用中划线`-`分隔，id则采用驼峰式命名规则；
* 慎用id，详见上一条 **【SEO 和预留】**

```html
<!-- Not recommended -->
<div class="j-hook left contentWrapper"></div>

<!-- Recommended -->
<div id="j-hook" class="sidebar content-wrapper"></div>
```

#### 属性顺序
HTML 属性应该按照特定的顺序出现以保证易读性。
* id
* class
* name
* data-xxx
* src, for, type, href
* title, alt
* aria-xxx, role

```html
<a id="..." class="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

#### 引号
属性的定义，统一使用双引号。

```html
<!-- Not recommended -->
<span id='j-hook' class=text>Google</span>

<!-- Recommended -->
<span id="j-hook" class="text">Google</span>
```

#### 嵌套 
`a 不允许嵌套 div`这种约束属于语义嵌套约束（**H5页面除外**），与之区别的约束还有严格嵌套约束，比如`a 不允许嵌套 a`。

严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

**语义嵌套约束**
* `<li>` 用于 `<ul>` 或 `<ol>` 下；
* `<dd>`, `<dt>` 用于 `<dl>` 下；
* `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<td>` 用于 `<table>` 下；

**严格嵌套约束**
* inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
* `<a>`里不可以嵌套交互式元素`<a>`、`<button>`、`<select>`等;
* `<p>`里不可以嵌套块级元素`<div>`、`<h1>~<h6>`、`<p>`、`<ul>/<ol>/<li>`、`<dl>/<dt>/<dd>`、`<form>`等。

更多详情，参考[WEB标准系列-HTML元素嵌套](http://www.smallni.com/element-nesting/)

#### 布尔值属性
HTML5 规范中 `disabled`、`checked`、`selected` 等属性不用设置值。
```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```
#### HTML 字符
HTML 字符： 特殊字符应尽量使用 HTML 定义的字符而不是直接使用文字；使用HTML 字符时，可以使用十进制编码格式或已有命名的实体，推荐使用前者。完整的HTML 字符集请参考附录：[常用 HTML 字符](http://www.w3school.com.cn/tags/html_ref_entities.html)。

### HTML 模板 （大招）
* uft-8模板 
	<!DOCTYPE html>
	<html>
		<head>
			<meta charset="utf-8" />
			<title>Title</title>
			<meta name="keywords" content="" />
			<meta name="description" content="" />
			<link href="css/metro.css" rel="stylesheet" />
		</head>
		<body>
			...
		</body>
	</html> 
	
* gbk模板 
	<!DOCTYPE html>
	<html>
		<head>
			<meta charset="gbk" />
			<title>Title</title>
			<meta name="keywords" content="" />
			<meta name="description" content="" />
			<link href="css/metro.css" rel="stylesheet" />
		</head>
		<body>
			...
		</body>
	</html>