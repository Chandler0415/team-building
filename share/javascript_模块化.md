##Javascript 模块化

*	模块化变化历程
	*	[前端模块化开发的价值](https://github.com/seajs/seajs/issues/547)
	*	蛮荒时代
				
		*	命名冲突
		*	依赖关系，js文件加载顺序
	*	函数包装
	*	命名空间
	*	匿名自执行函数

好处：	
	
*	关注度分离

*	CMD,AMD规范
	
	CommonJS和AMD是用于JavaScript模块管理的两大规范，前者定义的是模块的同步加载，主要用于NodeJS；而后者则是异步加载，通过requirejs等工具适用于前端。

	在实际项目中，代码以模块进行组织，AMD是在CommonJS的基础上考虑了浏览器的异步加载特性而产生的，可以让模块异步加载并保证执行顺序。而CommonJS的require函数则是同步加载。

	*	cmd
		
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
		
		```	
		

	*	AMD
		
		AMD设计出一个简洁的写模块API：

		**define(id?, dependencies?, factory);**


*	Require.js跟Sea.js







`资料`

*	[js模块历史](http://www.cnblogs.com/lvdabao/p/js-modules-develop.html)
*	[Javascript模块化编程（一）：模块的写法](http://www.ruanyifeng.com/blog/2012/10/javascript_module.html)
*	[AMD:浏览器中的模块规范](http://www.cnblogs.com/snandy/archive/2012/03/12/2390782.html)




