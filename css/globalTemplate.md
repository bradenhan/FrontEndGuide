# 通用模板 -- 必读大招


### **css模板**

css模板，其实就是reset。

由于不同浏览器对于同一标签的解析有差异，所以会导致页面展示差异，为了页面的统一性，我们必须使用** 统一 **的css reset。

### ** PC频道的reset **

```
/**
 * @Description: the stylesheet of XXX
 * @authors: XXX
 * @date   : XXX
 * @version: XX
 */
 
 
body,h1,h2,h3,h4,h5,h6,dl,dt,dd,ul,ol,li,th,
td,p,blockquote,pre,form,fieldset,legend,input,button,textarea,hr{margin:0;padding:0;}
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
如无特殊情况，** 前端频道必须使用此reset **。

### ** Wap站的reset **  

```
/**
 * @Description: the stylesheet of XXX
 * @authors: XXX
 * @date   : XXX 
 * @version: XXX 
 */
 
/*reset*/ 
html,body,header,footer,section,div,p,figure,ul,ol,li,h1,h2,h3,h4,fieldset,legend{margin:0; padding:0; font-size: 16px;}
html,body{height: 100%}
body{color: #333; font: 16px/1.5 "Microsoft YaHei",Arial; -webkit-text-size-adjust: none;}
ul,ol,li{list-style-type: none;}
em, i{font-style: normal;}
a, a:visited{color: #333;}
a, ins{text-decoration: none;}
a img{border: 0 none;}
article, aside, details, figcaption, figure,footer, header, hgroup, menu, nav, section{display: block;}
input{font-size: 16px; -webkit-box-sizing: border-box; -moz-box-sizing: border-box; box-sizing: border-box;}
input:focus::-webkit-input-placeholder{color: rgba(0,0,0,0);}
input::-webkit-input-placeholder{color: #999;}
input[type="button"], input[type="text"], input[type="submit"], input[type="tel"]{ -webkit-appearance: none; -moz-

appearance: none; -webkit-border-image: none; border-image: none; -webkit-border-radius: 0; border-radius: 0;}
.clearfix:after{content: ""; display: block; height: 0; overflow: hidden; clear: both; visibility: hidden;}
*{-webkit-tap-highlight-color:rgba(255,0,0,0);}
```
如无特殊情况， 移动端必须使用此reset 。