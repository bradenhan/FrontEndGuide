# css压缩

CSS压缩，包含CSS语法检查和CSS压缩，由于初涉此部分，所以，此部分暂时不支持IE7、IE6 hack，即：请前端同学尽量不要写带```*``` 和 ```_``` 为前缀的属性 。

### CSS语法检查

CSS压缩初步采用[Grunt](http://gruntjs.com/)的CSS插件【[grunt-contrib-csslint](https://www.npmjs.com/package/grunt-contrib-csslint)】进行语法检查。

使用方法：
+ 安装 csslint 插件：
  - ** npm install grunt-contrib-csslint --save-dev ** 
+ 在Gruntfile.js文件里面做如下配置：
    - 
     ```
     csslint:{
			build : ['Gruntfile.js','code/css/*.css'], //code/css/*.css 可做适当的调整
			options : {
				csslintrc : '.csslintrc'
			}
		}
        ```
    - 
    ```
    grunt.loadNpmTasks('grunt-contrib-csslint');
    ```
  
### CSS压缩

CSS压缩初步采用[Grunt](http://gruntjs.com/)的CSS插件【[grunt-contrib-cssmin](https://www.npmjs.com/package/grunt-contrib-cssmin)】进行CSS压缩。  
