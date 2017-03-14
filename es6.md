##let命令
	let声明的变量只在它所在的代码块有效。
	1
		var a = [];
		for (var i = 0; i < 10; i++) {
		  a[i] = function () {
		    console.log(i);
		  };
		}
		a[6](); // 10
		变量i是var声明的，在全局范围内都有效。所以每一次循环，新的i值都会覆盖旧值，导致最后输出的是最后一轮的i的值。	
	2
		var a = [];
		for (let i = 0; i < 10; i++) {
		  a[i] = function () {
		    console.log(i);
		  };
		}
		a[6](); // 6
		变量i是let声明的，当前的i只在本轮循环有效，所以每一次循环的i其实都是一个新的变量，所以最后输出的是6。

##不存在变量提升
	var命令会发生”变量提升“现象，即变量可以在声明之前使用，值为undefined。这种现象多多少少是有些奇怪的，按照一般的逻辑，变量应该在声明语句之后才可以使用。
	
	为了纠正这种现象，let命令改变了语法行为，它所声明的变量一定要在声明后使用，否则报错。
	
	// var 的情况
	console.log(foo); // 输出undefined
	var foo = 2;
	
	// let 的情况
	console.log(bar); // 报错ReferenceError
	let bar = 2;

	上面代码中，变量foo用var命令声明，会发生变量提升，即脚本开始运行时，变量foo已经存在了，但是没有值，所以会输出undefined。变量bar用let命令声明，不会发生变量提升。这表示在声明它之前，变量bar是不存在的，这时如果用到它，就会抛出一个错误。