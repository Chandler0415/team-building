##Javascript 模块化

*	模块化变化历程

	*	蛮荒时代			
		*	命名冲突
		*	依赖关系，js文件加载顺序
		*	无法有效重用
		*	代码组织混乱
	*	对象写法
	
	```
	//方式1
	
	var pageView = new Object({
		name: 'page view',
		init: function(){},
		getName: function(){}
	});
	
	//方式二
	var student = {
		name: '',
		checkName: function(){
			return /\w+/g.test(this.name);
		}
	};
	
	```
	
	*	函数包装
	
	```
	var Calc = function() {
		var num1, num2;
		
		return {
			init: function(n1,n2){
				num1 = n1;
				num2 = n2;
			},
			add: function(n){
				return num1 + num2 + n;
			}
		};		
	};
	
	
	Calc.init(1,3);
	
	```
	
	*	命名空间
	
	```
	var YYT = {};
	YYT.tools = {};
	YYT.views = {};
	
	YYT.tools.md5 = function(val){
		return val;
	};
	
	YYT.views.getAll = function(){
		//do something
	};
	
	```
	
	
	*	匿名自执行函数
	
	```
	
	//基本用法
	var teacher = (function(){
		var total = 0;
		
		var fun1 = function(){
			//
		};
		
		var fun2 = function(){
		};
		
		return {
			fun1: fun1,
			fun2: fun2
		};
		
	})();
	
	
	// 加载外部模块，改变全局变量
	var app = (function($, Backbone, app){
		app.version = '1.0.1';
		
		var view = Backbone.View.extend({
			$el: ''
		});
		
		$(function(){
			console.log('ready');
		});
	
	})(jQuery,Backbone, window.app || {});
	
	
	```
	
`模块化好处：`	
	
*	关注度分离

*	易于维护



###CMD,AMD规范
	
CommonJS和AMD是用于JavaScript模块管理的两大规范，前者定义的是模块的同步加载，主要用于NodeJS；而后者则是异步加载，通过requirejs等工具适用于前端。

在实际项目中，代码以模块进行组织，AMD是在CommonJS的基础上考虑了浏览器的异步加载特性而产生的，可以让模块异步加载并保证执行顺序。而CommonJS的require函数则是同步加载。

*	CMD
		
	起源于node.js
		
	```
		//math.js
		exports.add = function() {
			var sum = 0, i = 0, args = arguments, l = args.length;
    		while (i < l) {
        	sum += args[i++];
    		}
    		return sum;
		};
		
		//increment.js
		var add = require('math').add;
		exports.increment = function(val) {
		    return add(val, 1);
		};
		
		//program.js
		var inc = require('increment').increment;
		var a = 1;
		inc(a); // 2
		
	```	
		

	*	AMD(Asynchronous Module Definition)
		
		AMD设计出一个简洁的写模块API：

		**define(id?, dependencies?, factory);**




###Require.js

*	优化
	*		








`资料`

*	[js模块历史](http://www.cnblogs.com/lvdabao/p/js-modules-develop.html)
*	[Javascript模块化编程（一）：模块的写法](http://www.ruanyifeng.com/blog/2012/10/javascript_module.html)
*	[AMD:浏览器中的模块规范](http://www.cnblogs.com/snandy/archive/2012/03/12/2390782.html)
*	[前端模块化开发的价值](https://github.com/seajs/seajs/issues/547)



