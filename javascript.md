##true  false
	var undefined;
	undefined == null; // true
	1 == true;   // true
	2 == true;   // false
	0 == false;  // true
	0 === false; //false
	0 == '';     // true
	NaN == NaN;  // false
	[] == false; // true
	[] == ![];   // true


	undefined与null相等，但不恒等（===）

	一个是number一个是string时，会尝试将string转换为number
	尝试将boolean转换为number，0或1
	尝试将Object转换成number或string，取决于另外一个对比量的类型
	所以，对于0、空字符串的判断，建议使用 “===” 。“===”会先判断两边的值类型，类型不匹配时为false。
##纯函数  非纯函数
	非纯函数依赖window这个全局对象的状态来计算宽度和高度，而自给自足的纯函数则要求这些值作为参数传入，当一个函数是纯的，也就是不依赖于当前状态和环境，我们就不用管它实际的计算结果是什么时候被计算出来。

##js对比时间的例子
	<script>
        function compareTime(a, b) {
            var arr = a.split("-"); //log [2016,04,06]
            var start = new Date(arr[0], (arr[1] - 1), arr[2]);//月份的数值是从0到11之间的整数
            var starts = start.getTime(); //输出时间戳进行对比
            var arrs = b.split("-");
            var end = new Date(arrs[0], (arrs[1] - 1), arrs[2]);
            var ends = end.getTime();
            if (starts >= ends)
                console.log('开始时间大于结束时间');
            else
                console.log('开始时间小于结束时间');
        }
        compareTime('2016-05-03', '2016-05-04');
    </script>




	function compareTime(a, b) {
            var arr = a.split("-"); //log [2016,04,06]
            var start = new Date(arr[0], (arr[1] - 1), arr[2]);
            var starts = start.getTime(); //输出时间戳进行对比
            var arrs = b.split("-");
            var end = new Date(arrs[0], (arrs[1] - 1), arrs[2]);
            var ends = end.getTime();
            var weekDay = ["星期天", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"];
            //getDay() 方法可返回表示星期的某一天的数字。
            console.log("开始时间是" + weekDay[start.getDay()] + "\r\n" + "结束时间是" + weekDay[end.getDay()]);
            var now = new Date();
            console.log("现在是" + weekDay[now.getDay()]);
            if (starts >= ends)
                console.log('开始时间大于结束时间');
            else
                console.log('开始时间小于结束时间');
  	}
    compareTime('2016-05-03', '2016-05-04');
##use strict
	在strict模式下运行的JavaScript代码，强制通过var申明变量，未使用var申明变量就使用的，将导致运行错误。
##字符串
	`支持多行字符串
		alert(`多行
		字符串
		测试`);

		var name = '小明';
		var age = 20;
		alert(`你好, ${name}, 你今年${age}岁了!`);
		alert(`欢迎${arr[0]},${arr[1]},${arr[2]}和${arr[3]}同学！`);
##concat
	concat()方法并没有修改当前Array，而是返回了一个新的Array
	var arr = ['A', 'B', 'C'];
	arr.concat(1, 2, [3, 4]); // ['A', 'B', 'C', 1, 2, 3, 4]
##对象
	JavaScript规定，访问不存在的属性不报错，而是返回undefined
	
	***********检测某对象是否有一个属性，用in操作符**********
	
	var xiaoming = {
	    name: '小明',
	    birth: 1990,
	    school: 'No.1 Middle School',
	    height: 1.70,
	    weight: 65,
	    score: null
	};
	'name' in xiaoming; // true
	'grade' in xiaoming; // false

	****
			如果in判断一个属性存在，这个属性不一定是xiaoming的，它可能是xiaoming继承得到的，要判断一个属性是否是xiaoming自身拥有的，而不是继承得到的，可以用hasOwnProperty()方法
	
			var xiaoming = {
			    name: '小明'
			};
			xiaoming.hasOwnProperty('name'); // true
			xiaoming.hasOwnProperty('toString'); // false
	****
##if else
	else语句是可选的。如果语句块只包含一条语句，那么可以省略{}
##map

	var m=new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
	m.get('Michael')

初始化Map需要一个二维数组，或者直接初始化一个空Map。Map具有以下方法：

	var m = new Map(); // 空Map
	m.set('Adam', 67); // 添加新的key-value
	m.set('Bob', 59);
	m.has('Adam'); // 是否存在key 'Adam': true
	m.get('Adam'); // 67
	m.delete('Adam'); // 删除key 'Adam'
	m.get('Adam'); // undefined
##for ...of
	var a = ['A', 'B', 'C'];
	var s = new Set(['A', 'B', 'C']);
	var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
	for (var x of a) { // 遍历Array
	    alert(x);
	}
	for (var x of s) { // 遍历Set
	    alert(x);
	}
	for (var x of m) { // 遍历Map
	    alert(x[0] + '=' + x[1]);//输出结果为1=x 2=y  3=z
	}
##iterable
	新的iterable类型，Array、Map和Set都属于iterable类型。
	具有iterable类型的集合可以通过新的for ... of循环来遍历。
##forEach
	var a = ['A', 'B', 'C'];
	a.forEach(function (element, index, array) {
	    // element: 指向当前元素的值
	    // index: 指向当前索引
	    // array: 指向Array对象本身
	    alert(element);
	});
##set  forEach

	Set与Array类似，但Set没有索引，因此回调函数的前两个参数都是元素本身：

	var s = new Set(['A', 'B', 'C']);
	s.forEach(function (element, sameElement, set) {
	    alert(element);
	});
##Map forEach
	
	var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
	m.forEach(function (value, key, map) {
	    alert(value);
	});
##全局作用域
	不在任何函数内定义的变量就具有全局作用域。实际上，JavaScript默认有一个全局对象window，全局作用域的变量实际上被绑定到window的一个属性

	**for循环第一条语句声明的变量是全局变量，在for循环外面当然可以正常使用。
##变量提升
	变量提升与函数声明提升是JS设计的缺陷，在其他语言中直接就报错了

	不要使用变量提升与函数声明提升，所有变量和函数遵循先声明后使用的原则
	
	不要在JS的设计缺陷中纠结，知道后避开坑
##reduce
	var arr = [1, 3, 5, 7, 9];
	arr.reduce(function (x, y) {
	    return x + y;
	}); // 25
	
	function add(x,y,f){return f(x)+f(y)}
	add(-5,6,Math.abs)
##sort
	比较大小
	var arr = [10, 20, 1, 2];
	arr.sort(function (x, y) {
	    if (x < y) {
	        return 1;
	    }
	    if (x > y) {
	        return -1;
	    }
	    return 0;
	}); // [20, 10, 2, 1]
	
	****sort()方法会直接对Array进行修改，它返回的结果仍是当前Array：
##闭包

	在函数lazy_sum中又定义了函数sum，并且，内部函数sum可以引用外部函数lazy_sum的参数和局部变量，当lazy_sum返回函数sum时，相关参数和变量都保存在返回的函数中，这种称为“闭包（Closure）”的程序结构拥有极大的威力。

	返回闭包时牢记的一点就是：返回函数不要引用任何循环变量，或者后续会发生变化的变量。
##复制文本粘贴
	if(window.clipboardData){
		//for IE
		var copyBtn = document.getElementById("copy");
		copyBtn.onclick = function(){ 
			var text = $("#copy").attr("data-clipboard-text");
			window.clipboardData.setData('text',text); 
			alert("复制成功，内容为： " + text);
		} 
	}else{
		var client = new ZeroClipboard(document.getElementById("copy"));
		client.on("ready", function(readyEvent) {
			client.on("aftercopy", function(event) {
				alert("复制成功，内容为: " + event.data["text/plain"]);
			});
		});
	} 

	<dl>
		<dt>地址：</dt>
		<dd>
			<input type="text" name="address" class="required" size="30" value="<{$row.address}>" id="content" readonly/>
		</dd>
	</dl>
	<dl>
		<span class="jwd_tishi" id="copy" data-clipboard-target="content">复制地址</span>
	</dl>
##闭包
	for (var i = 0; i < 5; i++) {
	    (function(j) {  // j = i
	        setTimeout(function() {
	            console.log(new Date, j);
	        }, 1000);
	    })(i);
	}
	
	console.log(new Date, i);输出为5 0 1 2 3 4
##jquery源码
	（function(){
		(21,94) 定义了一些变量和函数  jQuery=function(){}
		(96,283) 给JQ对象，添加一些方法和属性
		(285,347) extend:JQ的继承方法
		(349,817) jQuery.extend():扩展一些工具方法
		(877,2856) Sizzle:复杂选择器的实现
		(2880,3042) Callbacks:回调对象：对函数的统一管理
		(3043,3183) Deferred:延迟对象：对异步的统一管理
		(3184,3295) support：功能检测
		(3308,3652) data():数据缓存
		(3653,3797) queue():队列管理
		(3803,4299) attr()  prop() val() addClass()等：对元素属性的操作
		(4300,5128) on()  trigger() :事件操作的相关方法
	}）();
##判断是否是创建标签
	selector.charAt(0)==='<'&&selector.charAt(selector.length-1)==='>'&&selector.length>=3
	
##jquery知识点
	正则：
		-webkit-margin-left:webkitMarginLeft
		/^-ms-/       -ms-margin-left:MsMarginLeft
		/-([\da-z])/  -2d:2d
	原型：
		function Aaa(){}
		Aaa.prototype.constructor=Aaa;Aaa的原型的构造方法指向Aaa;
	constructor:防止手动被改，需要重新指定
##jquery.merge
	true  可以执行script标签  <\/script>标签需要转义
	返回一个数组  
	var arr=['a','b'];
	var brr=['c','d'];
	$.merge(arr,brr)将两个数组合并