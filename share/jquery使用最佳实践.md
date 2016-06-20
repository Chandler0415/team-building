#jQuery使用最佳实践


####选择器

* Use ID selector whenever possible. It is faster because they are handled using document.getElementById().
* When using class selectors, don't use the element type in your selector. Performance Comparison 


```
var $products = $("div.products"); // SLOW
var $products = $(".products"); // FAST
```

*	Use find for Id->Child nested selectors. The .find() approach is faster because the first selection is handled without going through the Sizzle selector engine. More Info 

```
// BAD, a nested query for Sizzle selector engine
var $productIds = $("#products div.id");

// GOOD, #products is already selected by document.getElementById() so only div.id needs to go through Sizzle selector engine
var $productIds = $("#products").find("div.id");
```


* Be specific on the right-hand side of your selector, and less specific on the left. More Info 

```
// Unoptimized
$("div.data .gonzalez");

// Optimized
$(".data td.gonzalez");

```

*	Avoid Excessive Specificity.

```
$(".data table.attendees td.gonzalez");
 
// Better: Drop the middle if possible.
$(".data td.gonzalez");
```

*	Give your Selectors a Context.

```
// SLOWER because it has to traverse the whole DOM for .class
$('.class');

// FASTER because now it only looks under class-container.
$('.class', '#class-container');
```

*	Avoid Universal Selectors.

```
$('div.container > *'); // BAD
$('div.container').children(); // BETTER
```
*	Avoid Implied Universal Selectors. When you leave off the selector, the universal selector (*) is still implied

```
$('div.someclass :radio'); // BAD
$('div.someclass input:radio'); // GOOD
```



####DOM操作








`参考资料`]

*	[jQuery Coding Standards & Best Practices](http://lab.abhinayrathore.com/jquery-standards/)

