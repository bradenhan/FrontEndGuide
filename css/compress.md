# css压缩


###

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
				csslintrc : '.csslintrc' //此文件暂时未1.0版本，以后会不断完善
			}
		}
        ```
    - 
    ```
    grunt.loadNpmTasks('grunt-contrib-csslint');
    ```

  
