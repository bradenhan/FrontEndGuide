
# css压缩

CSS压缩初步采用[Grunt](http://gruntjs.com/)的CSS插件【[grunt-contrib-csslint](https://www.npmjs.com/package/grunt-contrib-csslint)】进行压缩。

使用方法：
+ 安装 csslint 插件：
  - ** npm install grunt-contrib-csslint --save-dev ** 
+ 在Gruntfile.js文件里面做如下配置：
    -Q csslint:{
			build : ['Gruntfile.js','code/css/*.css'],
			options : {
				csslintrc : '.csslintrc'
			}
		}
  
