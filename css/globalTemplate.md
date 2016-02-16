# 通用模板 -- 必读大招


### **css模板**

css模板，其实就是reset。

由于不同浏览器对于同一标签的解析有差异，所以会导致页面展示差异，为了页面的统一性，我们必须使用** 统一 **的css reset。

### ** PC频道的reset **

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
如无特使情况，** 前端频道必须使用此reset **。
  