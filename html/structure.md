# 模块化

`html` 尽量模块化去写，这样，能提高效率，便于以后维护。

#### 常见模块


*  新闻列表  (news-list)

页面展现形式：

![](https://bradenhan.gitbooks.io/front-end/content/img/news-list.png)

HTML结构：
```
<ul class="news-list">
	<li>
		<a title="脚尖上的甜点巴黎 学拍充满创意的美食作品" target="_blank" href="#">脚尖上的甜点巴黎 学拍充满创意的美食作品</a>
	</li>
	<li>
		<a title="性感是不言而喻的 自然随性的环境中拍情绪人像" target="_blank" href="#">性感是不言而喻的 自然随性的环境中拍情绪人</a>
	</li>
	<li>
		<a title="哈苏大师镜头下的森林 学拍光影和色彩的碰撞" target="_blank" href="#">哈苏大师镜头下的森林 学拍光影和色彩的碰撞</a>
	</li>
	<li>
		<a title="脑洞有多大 用剪影的形式来表现留白的意境" target="_blank" href="#">脑洞有多大 用剪影的形式来表现留白的意境</a>
	</li>
</ul>
```

	
*  图片列表 (pic-list)

页面展现形式：  
![](https://bradenhan.gitbooks.io/front-end/content/img/pic-list.png) 

HTML 结构
```
<ul class="pic-list clearfix">
	<li>
		<a title="成就最理想的工作 摄影师带你探寻风光意境美" target="_blank" href="http://academy.fengniao.com/532/5327301.html">
			<img width="140" height="105" alt="成就最理想的工作 摄影师带你探寻风光意境美" src="...">带你探寻风光意境美 
		</a>
	</li>
	<li>
		<a title="大片、大师、毒 浅谈中国摄影圈的一个特色 " target="_blank" href="http://academy.fengniao.com/532/5327233.html">
			<img width="140" height="105" alt="大片、大师、毒 浅谈中国摄影圈的一个特色 " src="...">中国摄影圈的一个特色 
		</a>
	</li>
</ul>
```

* 排行榜 (rank-list)

页面展现形式：  
![](https://bradenhan.gitbooks.io/front-end/content/img/排行榜.png)

HTML 结构
```
<ul class="rank-list">
	<li>
		<em class="n1">1</em>
		<a class="user" title="yu20051013" target="_blank" href="#" rel="nofollow">yu20051013</a>
		<a title="走进神秘非洲" target="_blank" href="#">走进神秘非洲</a>
	</li>
	<li>
		<em class="n1">2</em>
		<a class="user" title="diff007	" target="_blank" href="#" rel="nofollow">diff007</a>
		<a title="超短暂的宏村游" target="_blank" href="#">超短暂的宏村游</a></li>
	<li>
		<em class="n1">3</em>
		<a class="user" title="karen-qd" target="_blank" href="#" rel="nofollow">karen-qd</a>
		<a title="库车大峡谷" target="_blank" href="#">库车大峡谷</a>
	</li>
	。。。
	<li>
		<em>10</em>
		<a class="user" title="元阳梯田" target="_blank" href="#" rel="nofollow">元阳梯田</a>
		<a title="鸡鸣山下鸡鸣驿" target="_blank" href="#">鸡鸣山下鸡鸣驿</a>
	</li>
</ul>
```
* ##### 广告

页面展现形式：  
![](https://bradenhan.gitbooks.io/front-end/content/img/ad-div.png)

HTML 结构
```
<div class="ad-div">
	<div>
		<img src="###" width="###" height="###"/>
	</div>
</div>
```
CSS 代码：
```
.ad-div {font: 0/0 Arial}
.ad-div div {margin-top: 8px}

```
> ##### 页面模块  
 

### 更多

以待有缘人补充
 